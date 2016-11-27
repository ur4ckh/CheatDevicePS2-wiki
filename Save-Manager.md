The Save Manager allows save files to be transferred between memory cards and a flash drive.

# Supported Formats
* **CBS** - CodeBreaker Save. Uses ZLIB for compression.
* **ZIP** - Standard ZIP File. Best for long-term archiving and easy modification. [See note below](#note-about-zip-files)
* **PSU** - EMS Adapter Save. Simple format that doesn't use any compression.

# Known Bugs
* Amount of free space on flash drives can't be determined resulting in corruption if a file exceeding its remaining capacity is written.
* Contents of ZIP files assumed to be correct (1 directory with files) without checking.

# Note about ZIP files
As of November 27, 2016, Cheat Device now supports ZIP files for creating/extracting save files. The ZIP file is expected to contain one directory (with the same name used on the memory card's filesystem) containing all the necessary save files inside it. Cheat Device will create ZIP files in this manor, but if you create a ZIP file for saves outside of Cheat Device, make sure it follows this rule.