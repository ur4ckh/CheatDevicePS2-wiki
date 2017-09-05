Settings are stored in an ini file named `CheatDevicePS2.ini` in the directory Cheat Device is run from.
# [CheatDevicePS2]
* database = Path to .CDB or .TXT cheat database
* boot[0-4] = Paths to boot from when cheats are enabled in addition to the disk-boot option

# Default Values
If CheatDevicePS2.ini can't be loaded, these default values will be used instead:
* databasePath = CheatDatabase.cdb
* boot0 = mc0:/BOOT/BOOT.ELF
* boot1 = mc1:/BOOT/BOOT.ELF
* boot2 = mass:/BOOT/BOOT.ELF
* boot3 = rom0:OSDSYS
* boot4 = FASTBOOT