# Windows Fails to Boot — Troubleshooting Guide

**A practical, tested step-by-step guide** to diagnose and repair Windows systems that fail to boot, loop on startup, show a black screen, or display boot errors.  
Prepared and tested in a controlled lab environment.  


## 🚩 What This Guide Is For
**Goal:** Identify the causes and repair common Windows boot problems such as (corrupt BCD/MBR, disk errors, failed updates, driver issues).  
**Target audience:** Anyone learning IT or interested in desktop / helpdesk support.<br> 
**Estimated time:** 30–90 minutes (depending on how bad the system is)


## 📋 Common Symptoms
- Stuck at Windows logo with a spinning circle  
- The message "Automatic Repair couldn't repair your PC"  
- Black screen with a blinking cursor  
- Endless Boot loops or BSOD (blue screen of death) right after Windows Startup  
- The messages "No boot device found" or "Bootmgr is missing"


## 🛠 Prerequisites
- Windows installation USB or ISO if you're using a VM (virtual machine) 
- Access to BIOS/UEFI  
- Administrator Command Prompt (through recovery mode)
- Optional: Spare SATA cable or a known good drive if you suspect hardware issues


## 🔍 Quick Checklist
1. Does the BIOS/UEFI detect the Hard Drive (HDD) or Solid State Drive? (SSD)
2. Can you get into the WinRE (Windows Recovery Environment)?  
3. Is it a hardware issue (bad drive, faulty cable, faulty RAM) or is it a software one (corrupted boot files, corrupted updates, etc?)


## ✅ Fix Steps (Do these in order)

### 1 — Hardware & BIOS check
1. Completely power the PC off, unplug it and wait 10 seconds before plugging it back in.
2. Reseat your SATA/power cables and RAM. (Don't skip this step!)
3. Boot into BIOS and make sure the drive is actually detected.
4. If the drive isn't detected, try another cable or port. If it's still missing, test with another drive.


### 2 — Enter Windows Recovery Environment (WinRE)
- Power the computer on, then as soon as the windows logo appears, hold the power button to force it back off.  
- Do that until it triggers the "Preparing Automatic Repair"
- Once you're there, go to Advanced Options > Troubleshoot > Advanced Options.


### 3 — Run Startup Repair
- Select **Startup Repair** and follow prompts.  
- If this fails, record the error message and continue to manual repair below.


### 4 — Manual boot repair (Command Prompt)
Open the **Command Prompt** in WinRE and run:

```bash
bootrec /fixmbr
bootrec /fixboot
bootrec /scanos
bootrec /rebuildbcd
```

### 5 - If none of these steps seem to work, it's most likely a drive issue or a completely corrupted Windows. At that point, back up your data (if still possible) and simply reinstall. This guide should help you prevent the same issue in the future.

