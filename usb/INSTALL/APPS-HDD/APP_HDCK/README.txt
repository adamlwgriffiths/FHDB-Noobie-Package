HDDChecker v0.961	- 2018/06/20
------------------------------------

HDDChecker is a disk diagnostic tool meant for testing the health of your PlayStation 2 console's Harddisk Drive unit.
It now supports maintenance of the partitions on the disk too.

It was conceived and constructed because I didn't want to see anymore poor SCPH-20400 units being cut open,
just to have the disks within them taken out for testing. >_>

Features:
---------
1. Detects and lists the model, serial, firmware and S.M.A.R.T. status of HDD unit 0 (Primary Master).
2. Performs a surface scan of the disk.
3. Supports 48-bit LBA disks up to 2TB.
4. Performs zero-filling of the disk.
5. With the surface scan, bad sectors found might be remappable.
	Writing to a to-be-remapped sector (those hard-to-read sectors, as recorded by the disk)
		may kick off the actual sector remapping process.
	However, this has not been widely tested and is manufacturer-specific.
6. Checks for damage to the APA scheme and PFS partitions.
7. Optimizes the partitions on the HDD to reclaim space.

Notes/known issues/bugs:
------------------------
*Disks up to 2TB are supported. Any capacities beyond that will be truncated to 2TB.

*Do not use (usually old) disks that are not compliant with the ATA-4 specification.
 Like with every other PlayStation 2 software out there that supports the ATA interface, the disk is expected to support UDMA mode 4 and S.M.A.R.T.

*If the disk's S.M.A.R.T. status is indicated to be no good (NG status), the disk is about to fail and should be replaced.

*This tool may not be able to successfully remap sectors on all drives, as there isn't an official specification on remapping sectors within the ATA specification.
 If writing to a bad sector isn't sufficient to cause the disk to automatically remap it, the manufacturer's tools may have to be used instead.

*If a bad sector cannot be remapped, the disk is dying and should be replaced.

*As zeros will be written to the bad sector in an attempt to cause the disk to remap it, the data stored within the bad sector will be lost.
 Do not choose to remap the sector if it contains data that cannot be lost.

*As of the time of writing, only FHDB can boot HDDChecker correctly from the HDD unit.
 LaunchELF does not have full support for HDD-based paths, and cannot support HDDChecker.

Logging Feature
---------------
As of HDDChecker v0.96, a new logging feature has been added.

4 log files will be generated:
	When scanning is done:
		*hdck.log
		*fsck.log
	When optimization is done:
		*fssk.log
		*hdsk.log

No log files will be generated for surface scanning or zero-filling,
as the purpose of these log files is allow what was done during the scanning and optimization operations to be explained.

If you experience problems with HDDChecker's scanning and optimization functionality, please contact the developer and provide the log files.

How to setup this software:
---------------------------
Extract the main binary (HDDChecker.elf) and the lang folder (do not delete any files), and place both of them in the same place.
The only supported devices are the HDD unit, Memory Card and USB mass storage device.

Changelog:
----------
v0.961	- 2018/06/20
	*Added missing code for reloading the HDD modules, to allow the disk's format status to be refreshed after a disk erasure.

v0.961	- 2018/06/19
	*Fixed incorrect logic in UI, which causes the menu to be opened twice.

v0.961	- 2018/06/18
	*Fixed incorrect logic that prevent fsck from checking more than ~16 files in a directory.
	*Added option to format a HDD, if not formatted.
	*Updated translation template.

v0.96	- 2018/06/12
	*Added logging feature.
	*Fixed off-by-one error in fsck, which caused undefined behaviour.
	*Fixed incorrect logic if hdsk, which caused the simulated behaviour to not match the actual APA-level optimization operation.
	*Fixed progress computation jumping to random values or causing a freeze (division by 0).
	*Updated to build with the latest PS2SDK for updates to PFS.
	*UI update for nicer font-rendering.

v0.95	- 2018/02/04
	*Corrected logic error in HDSK simulation code (estimation for disk optimization part 2).
	*Updated to work with the latest PS2SDK revision: better stability and correctness of operation.
	*Replaced icons with new icons from Berion.

v0.942	- 2017/02/27
	*Corrected logic error in fsck.
	*Added new Italian localization by Vash The Stampede

v0.941	- 2016/12/16
	*Fixed coordinate overflow in font-drawing.
	*Rebuilt to not have the full kernel OSD patch (PS2SDK update).
		(prevents users of SCPH-10000/SCPH-15000 from being blocked from changing the language setting)

v0.941	- 2016/12/04
	*Fixed missing return value in HDD.IRX.
	*Added more comments to FSCK.
	*Changed some code to avoid potential mismatched-sign comparisons.

v0.94	- 2016/09/16
	*Removed limitation on optimizing disks with HDLoader games.
	*Added unofficial support for optimizing HDLoader games to hdsk.
	*Added a 2TB capacity limit.
	*Removed unused size labels.
	*Updated to compile with the latest PS2SDK changes.
	*Added updated German, French and Spanish localizations.
	*Corrected error in Portuguese localization.
	*Corrected sector error check.
	*Added workaround for the PSX to the scanning and zero-filling.
	*Removed Japanese font. Will re-add if a localization is added.
	*Changed font support to not store the whole font in RAM, unless the tool is booted from the HDD unit.
	*If booted from the HDD unit, the whole font file is read into memory.
	*Changed UI initialization code to allow the font to be re-opened after IOP reboots.
	*Expanded initialization thread's stack size to correct stack overflow.
	*Added missing disk check status labels.
	*Added a display for the number of errors found.
	*It is no longer considered an error, if the number of errors fixed is not equal to the number of errors found.
	*The cancel button is no longer fixed to CROSS for all operations.
	*Corrected progress bar display during disk optimization.
	*PS2SDK APA update: fixed incorrect behaviour of HIOCGETPARTERROR.
	*Improved efficiency of VRAM storage for fonts.

v0.932	- 2016/08/09
	*Relocated the version number.
	*Fixed size calculation error in fsckFixDEntry() of fsck.
	*Fixed cosmetic errors in disassembly of fsck.
	*Updated to have the latest PS2SDK changes.
	*Added Spanish and German localizations.
	*Updated Portuguese localization.

v0.931	- 2016/06/09
	*Only the "OK" button legend will be displayed for information (single-option) messages.
	*No button legend will be displayed for status updates (i.e. "Please wait..." screens).
	*The last-accessed menu will be displayed, upon the user returning to the menu.
	*The last-selected menu option will be highlighted, upon the user returning to the menu.
	*Long messages and labels will now be once again automatically wrapped.
	*Removed support for the tab ("\t") escape character in translation files.
	*Removed workarounds for clone/compatible network adaptors.
	*Ported workaround for the PSX's DVRP.
	*Changed "NG" to "FAIL", and added "PASS".

v0.93	- 2016/01/09
	*Added animations to UI.
	*Select button will be CIRCLE for Japanese consoles and CROSS for everything else.
	*Shifted the PAL screen to the right by 4.
	*Re-added quit confirmation message.

v0.93	- 2016/01/06
	*Fixed language support.

v0.93	- 2016/01/01
	*Updated to compile with the new PS2SDK.
	*Renamed to HDDChecker.
	*Revamped UI.
	*Rewritten to use libgs, so gsKit is no longer required.
	*Added hdck (APA checker), fsck (PFS checker), hdsk (APA defragmenter) and fssk (PFS trimmer).
	*Changed fonts to the Google English and Japanese Noto fonts.
	*Added support for booting from the HDD unit.

v0.92	- 2014/06/23
	*Updated to compile with the new PS2SDK.
	*Ported over the updates to ATAD from the PS2SDK.
	*Attempted to add support for the VERIFY_SECTORS_EXT command, which was previously missing.

v0.91	- 2013/08/06 (Initial public release)
	*Zero filling and scanning operations can be aborted.
	*Updated ATAD module (See PS2SDK updates for yesterday).
	*Adjusted code a little in an attempt to make the estimated time remaining counter more accurate.
	*Added button icons.

v0.90	- 2013/08/05 (Initial release)

Credits:
	This software would not have been possible without the support of other users. Special thanks to:
		Berion, for the icons.
		krHACKen, giving reports on the S.M.A.R.T. status bug and contributing research materials.
		... and all beta testers!
