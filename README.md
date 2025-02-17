# Guide for unlocking BIOS in Lenovo G500

I'm making this guide for anyone who wants to unlock the BIOS in the Lenovo G500 so they can install a new wifi card. I didn't want to pay so I investigated quite a lot so here is all I retrieved. You still need to dirt your hands a bit with code but at least you will know what to do and have all the needed programs.

This method doesn't need a ISP programmer, but in case it doesn't work you will need one and research for that method.

Also this is exclusive for the G500 model, but it could work for other similar Lenovo models. You will need to do a bit of investigation there to know if it applies to your model.

All the software I used is on the [Software](https://github.com/jfernando-huarezr/unlock-bios-g500/tree/main/Software) folder in this repo. The main software is on the first level, and there is also a sub-folder with some software you may or may not need in case you arrived here after you tried something yourself.

## What we will need to do:

- A backup of your current BIOS. 
- Modify this BIOS you dumped, so we can bypass the wifi whitelist. 
- After we modify the BIOS nice and clean, we need to flash it.

And that´s it

## BIOS Backup

First we need to dump the BIOS. I used BACKUP_Tools19p. Just run it as admin, and it will create a results.rar in the Desktop. Decompress it and you will see a .bin file there. That's your BIOS backup file. In my case it was x64_bios-region_8.1.60.1561.bin

## Unlock the BIOS file

After that you need to follow this [excelent guide](https://medium.com/@p0358/removing-wlan-wwan-bios-whitelist-on-a-lenovo-laptop-to-use-a-custom-wi-fi-card-f6033a5a5e5a) to modify the .bin file we just created, so we can get the modified BIOS we will flash later. I uploaded the software needed, except IDA View. You need to download that one from https://hex-rays.com/ida-free. The free version is enough.

This is the trickiest part, but just follow the linked guide and you should be fine. Re-read it if needed until you get it.

## Flash the new BIOS

This is the easiest part, but the one where I got stucked for days because i couldn't find a place with all the information, just bits here and there. So here I'm helping you with what you need to do to flash your new modified BIOS:

- First donwload [Rufus](https://rufus.ie/en/). We need it to create a FreeDOS bootable USB drive
- Once you created the bootable USB, copy the files from the FPT folder into it. You see there is a bios.bin file, right? You need to replace it with your own modified bios you created. Don't use the default one, that one is only for my laptop and will not work on yours.
- Now you need to restart your Laptop and boot from the USB. Probably you will need to change the type of boot from UEFI to Legacy, so if it isn't booting check that first in your BIOS Menu and change that.
- Once you booted from the USB, you will see a command line. First, we need to run  **"prr2.exe"**, so we can bypass the "Error 28: Protected Range Registers". Just type "prr2.exe" and press Enter.
- If all is well, it will say you bypassed the problem. Now it's showtime, type **"flash.bat"** and it will flash your modified BIOS. Just wait until it finish. 
- Once it finish, that should be it. Just power off your Laptop, change the wifi card and boot it up. 

**Congratulations you have now an up to date Wifi Card!**
