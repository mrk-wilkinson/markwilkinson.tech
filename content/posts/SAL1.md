+++
title = "SAL1: My thoughts and how I studied"
draft = false
date = 2025-03-10
tags = ["Tryhackme", "Certifications", "SAL1"]
+++

## TLDR
In case you are studying for the exam right now and need to cram, I highly reccomend doing the challenge rooms on the SOC level 1 tryhackme path, doing the 2 available soc simulator scenarios on tryhackme, and taking a CySA+ practice quiz for the multiple choice.

## Style of the Exam

The exam consisted of
- A 80 multiple choice section worth 20% (1 hr)
- A soc-simulator scenarios worth 40% (1-2 hrs)
- Another soc scenario worth 40% (1-2 hrs)

## MCQ
The multiple choice was similar to the CySA+ multiple choice questions, however I felt some of the SAL1 questions went more practical with questions on tools while I felt the CySA+ was more theory and definitions.  None of the multiple choice questions required that much time and were mostly "you either know it or you don't" questions.

## The Soc Simulator
This is definitely TryHackMe's biggest selling point. Using the simulator it definitely felt more like a real SOC-Analyst job.  I do think the 2 simulations were too easy.  The only thing I really had to use aside from the alert queue was the tool in the VM to check if an ip was malicious.  None of the alerts required any in-depth analysis and were pretty obvious.  The majority of the scoring wasn't in correct identification, but in report writing and if you chose correctly to escalate an alert or not.  I think is a good balance as the simulator provides clear documentation on the simulated companies policy on escalation and other soc-notes that I found to be helpful.

## Studying for the sal1
Some of the things I did to study:
- TCM-Security SOC Analyst 101 course
- TryHackMe Soc Simulator (Both of the available scenarios)
- Reviewewd a CySA+ cheatsheet (Helpful for vocab)
- Completed some of the challenges in the THM Jr. SOC Analyst path
I Felt all of the resources I used gave me enough knowledge and background to pass the exam easily.  If I was to reccomend someone 
how to study for the exam I would suggest:
- Completing the THM Jr. SOC Analyst path (If you have prior knowledge, maybe only complete the challenges)
- Complete both of the SOC Simulator scenarios (Make sure you check your escalation and report writing, these are weighted heavily on the exam)

## Final Conclusion and Opinions
The main selling point of the certification is the SOC Simulator.  While it was cool and felt very practical, I feel there was a lot
more that could be done with it.  I only used the integrated splunk to check my work and never needed it to make a determination
on an alert.  I felt a lot more could have been done with the analyst VM, I only used it to check if an IP was malicious, which 
never ended up changing my determination on an alert, just provided more details to write on my alert report.  However, this is a
junior level certification, so most of this makes sense.  I have high hopes for the more advanced blue team certification (if they release one).