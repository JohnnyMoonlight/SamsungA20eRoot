# Rooting Samsung A20e
This Repositoriy contains a quick wrap up of rooting a Samsung A20e with Magisk and Odin on a Linux distro.

## 0. Preliminaries
Unlock OEM-Bootunloader on the mobile.
Create folder "src" on laptop.

## 1. Magisk 
Download [here](https://github.com/topjohnwu/Magisk/releases/tag/v27.0).

Copy to "src". 

## 2. Odin

Download odin4 from [here](https://xdaforums.com/t/official-samsung-odin-v4-1-2-1-dc05e3ea-for-linux.4453423/). Direct download link [here](https://xdaforums.com/attachments/odin-zip.5629297/).
Set executable bit (chmod +c ./odin4). Copy in file tree one level below "src".

## 3. SamFW

Download Stockroms from [here](https://samfw.com/firmware/SM-A202F/DBT/A202FXXU5CWF2?__cf_chl_rt_tk=RyLY9LEbj5H0wjL5V7tS..5R26H9ZOkqlA830tWbriI-1721066528-0.0.1.1-6057).

Copy to "src".

## 4. Patch AP-File

Copy both "AP_A202FXXU5CWF2_CL26555245_QB67141591_REV00_user_low_ship_meta_OS11.tar.md5" and magisk onto mobile phone.
Switch from laptop to mobile: first, install magisk from apk. Start Magisk, select install without recovery. Select copied AP-file. When done, magisk created a patched AP-version in the Download-folder on the mobile. Copy patched magisk AP-file from "Download"-Folder to "src".

## 5. Flash Mobile

Shutdown mobile. Remove USB-cable.
Enter "Download"-mode: hold both volume-buttons. While holding both buttons, connect mobile to laptop.
Download mode starts. 

To flash, use the following command on the laptop command line. Note, the AP-File is the patched magisk AP-file, not the stock AP-file, see the "-a"-parameter in the command.

`./odin4 -c ./src/a20e/SAMFW.COM_SM-A202F_DBT_A202FXXU5CWF2_fac/CP_A202FXXU5CWF1_CP24415051_CL26555245_QB66592928_REV00_user_low_ship.tar.md5 -a ./src/magisk_patched-27000_K238j.tar -b ./src/SAMFW.COM_SM-A202F_DBT_A202FXXU5CWF2_fac/BL_A202FXXU5CWF2_CL26555245_QB67141591_REV00_user_low_ship.tar.md5 -s ./src/SAMFW.COM_SM-A202F_DBT_A202FXXU5CWF2_fac/CSC_OMC_OXM_A202FOXM5CWF2_CL26555245_QB67141591_REV00_user_low_ship.tar.md5`

The device reboots, when mobile turns black press "volume up" and "power on".
System should enter recovery mode, execute factory reset with "Wipe data/factory reset".

Afterwards, setup the mobile device. Reinstall magisk (copy from "src" to device, install).

**Done**, Root access acquired.

## 6. Emergency

When stuck in bootloop or whatsoever, flash stockrom:

Recovery:

`./odin4 -c ./src/SAMFW.COM_SM-A202F_DBT_A202FXXU5CWF2_fac/CP_A202FXXU5CWF1_CP24415051_CL26555245_QB66592928_REV00_user_low_ship.tar.md5 -a ./src/SAMFW.COM_SM-A202F_DBT_A202FXXU5CWF2_fac/AP_A202FXXU5CWF2_CL26555245_QB67141591_REV00_user_low_ship_meta_OS11.tar.md5 -b ./src/SAMFW.COM_SM-A202F_DBT_A202FXXU5CWF2_fac/BL_A202FXXU5CWF2_CL26555245_QB67141591_REV00_user_low_ship.tar.md5`

## 7. Further things to do from here:

Install adb on laptop: `sudo apt-get install android-tools-adb`

Start shell connection to mobile `adb shell`

Start root session `su` (after execution confirm in magisk on mobile)

Hack stuff :)
