The Save Manager allows save files to be transferred between memory cards and a flash drive.

## Supported Formats

* **CBS** - CodeBreaker Save. Uses ZLIB for compression.
* **ZIP** - Standard ZIP File. Best for easy modification. [See note below](#note-about-zip-files)
* **PSU** - EMS Adapter Save. Simple format that doesn't use any compression.
* **MAX** - Action Replay MAX save. Only reading is supported.

## Known Bugs

* **There have been reports of the USB driver corrupting flash drives when exporting saves. As of July 22, 2018 Cheat Device is using the USBD.IRX and USBHDFSD.IRX modules provided by PS2SDK, but please use this at your own risk!**
* Amount of free space on flash drives can't be determined resulting in corruption if a file exceeding its remaining capacity is written.
* Contents of ZIP files are assumed to be correct (1 directory with files) without checking.

## Note about ZIP files

As of November 27, 2016, Cheat Device now supports ZIP files for creating/extracting save files. The ZIP file is expected to contain one directory (with the same name used on the memory card's filesystem) containing all files used by the save. Cheat Device will create ZIP files in this manner, but if you create a ZIP file for saves outside of Cheat Device, make sure it follows this rule.