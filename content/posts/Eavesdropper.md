+++
title = "Eavesdropper"
draft = false
date = 2026-02-04
tags = ["Tryhackme"]
+++

## Medium level challenge tryhackme room

**Context**
You've uncovered a user's (Frank) SSH private key and broken into a target environment. You have access as Frank but need to obtain root access.

My thoughts: Appears to be a straightforward linux privilege escalation challenge.


**Initial steps**
First I adjusted permissions on the SSH key to make it usable and then connected in. 
```
chmod 600 (key_name)
ssh -i (key_name) frank@TARGET_IP
```

Once I gained access as Frank I ran `id` and saw he was part of the sudo group.  Which normally would be helpful but without his password won't do much in this situation.
Unfortunately the sudoers file cannot be read, but standard practice would be
anyone in the sudo group can use sudo on any command, with password.

I ran `ps aux` to see if there was anything interesting running and it was the opposite.  Nothing.
So I decided it was time for old reliable, LinPEAS.


**LinPEAS**
```
scp linpeas.sh frank@TARGET_IP:/tmp/peas.sh
```

A quick scp lets us transfer the script onto the box.  After running the script and doing some general poking around, we aren't always the only ssh session.
Occasionally there is another ssh connection, and if we can eavesdrop on it, we might be able to get the password.

```
watch -n 1 ps aux
```
![Image of ps aux cmd](../../assets/eavesdropper1.png)

**Sniffing SSH**

I found this great article online talking about the process.
[https://networklogician.com/2021/04/17/sniffing-ssh-passwords/]
Now unfortunately that method requires root access, something we lack.

However, the article below gave me another method.  Changing the user profile to log a session.
[https://www.infosecmatter.com/ssh-sniffing-ssh-spying-methods-and-defense/]

That idea also failed, I ran `watch -n 1 ps aux` and saw the sessions were short, notty sessions so my profile trick would do nothing.

Unfortunately, sniffing the ssh connection doesn't seem like it will work.

We need to find out what is happening in these frequent, short connections.


**pspy**

Pssss.  Its time to spy.
[https://github.com/DominicBreuker/pspy]

Just running pspy should give you what you need, specifically, the command being automated
```
sudo cat /etc/shadow
```

Definitely a strange command to be automated, but whatever.

One of the main attack vectors of automated commands (like this, cronjobs, etc) is path.
If we can overwrite the path for the frank user (hey thats us!) we can change the binary it runs.

If we replace sudo with a script of our own, to say, get an input and write it to a text file.  We could get Frank's password.


**Sudo Hijacking**

First, we need to create our own sudo executable.

A bash script with the name sudo in the temp directory we make executable will work.

![bash script to mimic sudo](../../assets/eavesdropper2.png)

Now, we can add this line to the top of the bashrc to make the automation run our sudo before the real one.
```
PATH="/tmp:$PATH"
```

And after a little bit of waiting, the automation runs our sudo file.  If we check in the /tmp folder we find the file with the password.  This lets us sudo into the root user and read the flag!

![Terminal showing flag and successful sudo su cmd](../../assets/eavesdropper3.png)




