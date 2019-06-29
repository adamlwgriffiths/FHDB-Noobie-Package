HDLoader game installer v0.821	- 2018/12/08
--------------------------------------------

The HDLoader game installer allows the user to install PlayStation 2 games onto the installed Harddisk Drive,
for direct booting with the HDD Browser v2.00 update.

It can also be used as an alternative to HDLDump, as this software does not use the HDLDump protocol
and hence entirely uses TCP for reliable data transfer.

How to setup this software
--------------------------
Extract the main binary (HDLGameInstaller.elf) and the lang folder (do not delete any files),
and place both of them in the same place.
The only supported devices are the Memory Card and USB mass storage device.

Notes on network support
------------------------
*HDLGameInstaller now maintains its own network configuration file on the HDD unit.
*If you have not configured HDLGameInstaller before, your existing homebrew network settings will be automatically imported from IPCONFIG.DAT.
*Network settings can now be configured from the Options menu.
*Please ensure that TCP ports 45061 and 45062 are allowed in your network.
*If you use the Windows Firewall, you may have to allow "public" access for HDLGManClient.exe.

Prerequisites
-------------
1. A PlayStation 2 console.
2. A HDD unit and network adaptor (clones MAY/MAY NOT work).
3. A working HDDOSD installation
   Not strictly required, but required if you want to boot games from a browser-like menu.

Features
--------
1. Installs all PlayStation 2 games from the CD/DVD drive.
2. Installs all PlayStation 2 games remotely from a PC, over a network.
3. Installed games can be booted directly from the HDD browser.
4. Allows the user to manage instaled games locally, on the PlayStation 2 console itself.
5. Allows the user to manage installated games remotely from a PC, over a network.
6. Network performance uses the latest ethernet modules from the PS2SDK, giving about 6MB/s.
7. Allows the user to specify the savedata icon to use with the game.
8. Supports games >4GB in size and DVD9 games.
9. Game list can be sorted alphabetically (controlled from the PlayStation 2).
10. Supports the Dynamic Host Configuration Protocol (DHCP), for easy set up.

Settings are now saved into the HDLGameInstaller save data folder:
	hdd0:__common/Your Saves/HDLGAMEINSTALLER
If you wish to delete the save, you may do so with the HDD Browser or compatible homebrew (e.g. LaunchELF).

Supported Devices
-----------------
HDLGameInstaller may be installed (copied) onto and can be booted from:
* USB Mass Storage Devices.
  - Only USB disks are supported.
  - Multi-function devices are not supported.
  - Disk must have only one partition. Otherwise, the first partition will be accessed.
* PlayStation 2 HDD Unit.

Other devices are not supported.

Limitations/bugs
----------------
* The icon preview is messed up and is known to cause freezes.
  I don't have the knowledge nor resources to commit towards fixing it up. Someone else will have to solve this, sorry.
* The UI isn't the nicest one, but it works.
* No Japanese input support on the PS2 installer's end.
* DVD9 games can only be correctly installed from the PC client only, as the CDVDMAN module within the boot ROMs of all consoles does not support DVD9 layer 1.
* Not compatible with the APAEXT partitioning scheme (ToxicOS).
  !!!Do not use this software with a disk formatted with that scheme or data loss will occur!!!
* As the variable-width font may result in an uneven number of characters being displayed on the screen as a line is scrolled,
  the user may observe that the cursor might jump back by one place while scrolling. This is not a bug.

Credits:
	This software may have been worked on mainly by me, but I had the support of other users:
		l_Oliveira, for providing a number of test reports and giving suggestions for its design.
		Berion, for the icons.
		"Someone who wishes to remain anonymous".
		Jimmikaelkael, for open-ps2-loader (OPL). OPL is used for making the installed games bootable.
		Maximus32, for showing me how the network subsystem should be done.
		All translators and everybody who helped with multi-language support.
		... and all testers!
