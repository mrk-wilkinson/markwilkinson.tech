+++
title = "Thinkpad T580 - BIOS Update"
draft = false
date = 2026-02-12
tags = ["Thinkpad", "Laptop", "bios"]
+++

## Thinkpad T580 BIOS Update from Not-Windows

**The Problem**

Lenovo provides two ways to update the bios from their support website.

1. A Windows .exe program
  > I don't use windows so this was a non starter
2. A bootable CD ISO image
  > For some reason I just couldn't get this to work.  Even after extracting the ISO file it just appeared empty on my system.


**My Solution**

I run Windows on Docker so I can access Windows apps as needed on my system.  Running the Windows BIOS update program from there I selected Extract instead of Install and took a look at the files.

The extracted files included a README that said to run their script and point it at a FAT32 USB drive.  I didn't want to pass through a USB so I took a look at the script.  The only thing it does is copy select directories and files into the directory (in this case expecting a drive) you give it.

I pointed the script at a folder I made and transferred those files over to Linux.  I made a GPT partition table with one FAT32 partition on my USB drive and copied the files onto it.

Suprisingly worked easier than I expected, but took a while to figure out the initial path of running the Windows EXE and using the extract feature.  Booting the USB drive works as normal, make sure UEFI/both is selected for boot type in BIOS.  All you have to do after booting the drive is select 2 and hit enter a few times following on screen prompts.  MAKE SURE TO STAY PLUGGED IN AND HAVE A FULL BATTERY.

