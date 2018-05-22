Settings are stored in a file named `CheatDevicePS2.ini` in the directory Cheat Device is run from.

# [CheatDevicePS2]
* database = Path to a cheat database. A list of compatible formats can be found [here](https://github.com/root670/CheatDevicePS2/wiki/Cheats).
* boot[0-4] = Paths to ELF files to boot from when cheats are enabled in addition to the disk-boot option

# Default Values
If the settings file can't be loaded, these default values will be used instead:
* database = CheatDatabase.cdb
* boot0 = mass:/BOOT/BOOT.ELF
* boot1 = mass:/BOOT/ESR.ELF
* boot2 = mc0:/BOOT/BOOT.ELF
* boot3 = mc1:/BOOT/BOOT.ELF
* boot4 = rom:osdsys