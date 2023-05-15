
#### RAM upgrade

I've added 64 gigs of RAM from the other Gill Lab machine to the server I'm setting up.
Total RAM: 128 gb

### RAID setup

Setting up raid 1 on the 2 samsung 1TB evo ssds using the onboard Intel Rapid storage technology SCO option ROM 3.2.0.1022. Volume name  = `bagOfHolding`

To get to the raid menu:
	- let it boot without going into BIOS settings
	- press ctr+I on the drive info splash screen

#### ERROR NOTE:

rhel 8 does not recognise the sas controller on the dell presision7600 by default. 
https://www.dell.com/community/Precision-Fixed-Workstations/Intel-C600-Series-Chipset-SAS-RAID-Controller-for-Dell-T7600/td-p/7517094
You will need to get the driver from elrepo. 

Append this command after hitting `tab`  on the install splash screen. *Note: This is not possible if BIOS is set as UEFI, set BIOS back to legacy to access the tab screen*

inst.dd=https://elrepo.org/linux/dud/el8/x86_64/dd-isci-1.2.0-10.el8_7.elrepo.iso

Verifed that this works. If kernel is updated a newer SAS driver will be required find one here https://elrepo.org/linux/dud/el8/x86_64/ and replace the url in the command above. 

root password: guest
# CHANGE THIS!!!


**May 12th**

Registered the rhel install to my account with username: prince.apple.john@gmail.com
Necessary to get `yum` to work. -- change at some point to university account.

Installed `Tcl` and `Ksh`, created a lab user account `cdsadmin` with sudo access.  


## SSH + VNC setup

**May 16th**

ssh setup complete and verified

updated all software through the webcokpit for rhel

system crash/kernel panic on reboot, no clue why. 

Boots into rhel with no errors in version 3.1.el8  and rescue but crashes with the default boot option version `4.18.0-425.19.2.el8_7.x86_64

 I've changed this to `3.1.el8` so that default boots and not crashes. 

**This is how it is done**
```
[prince@localhost ~]$ sudo grubby --info=ALL | grep title

**title**="Red Hat Enterprise Linux (4.18.0-425.19.2.el8_7.x86_64) 8.7 (Ootpa)"

**title**="Red Hat Enterprise Linux (4.18.0-425.3.1.el8.x86_64) 8.7 (Ootpa)"

**title**="Red Hat Enterprise Linux (0-rescue-e51dd064914944b29a5af109dcad2304) 8.7 (Ootpa)"

[prince@localhost ~]$ sudo grub2-set-default 1

[prince@localhost ~]$ sudo grubby --default-kernel

/boot/vmlinuz-4.18.0-425.3.1.el8.x86_64
```

