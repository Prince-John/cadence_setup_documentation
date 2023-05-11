
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

You will need to get the driver from elrepo. 

Append this command after hitting `tab`  on the install splash screen. *Note: This is not possible if BIOS is set as UEFI, set BIOS back to legacy to access the tab screen*

inst.dd=https://elrepo.org/linux/dud/el8/x86_64/dd-isci-1.2.0-10.el8_7.elrepo.iso

Verifed that this works. If kernel is updated a newer SAS driver will be required find one here https://elrepo.org/linux/dud/el8/x86_64/ and replace the url in the command above. 

root password: guest
# CHANGE THIS!!!

