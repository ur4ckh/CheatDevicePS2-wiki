Settings are stored in a file named `CheatDevicePS2.ini` in the directory Cheat Device is run from. If the settings file can't be loaded, or an entry is missing, default values will be used instead.

## [CheatDevicePS2]

|Key|Description|Default Value|
|---|---|---|
|databaseReadOnly|Path to read-only cheat database|*(none)*|
|databaseReadWrite|Path to read-write cheat database|*(none)*|
|boot0|ELF file path|`mass:/BOOT/BOOT.ELF`|
|boot1|ELF file path|`mass:/BOOT/ESR.ELF`|
|boot2|ELF file path|`mc0:/BOOT/BOOT.ELF`|
|boot3|ELF file path|`mc1:/BOOT/BOOT.ELF`|
|boot4|ELF file path|`rom:osdsys`|

## Notes
* Paths to files on `mass:`, `mc0:`, `mc1:`, `host:`, `rom:`, and `cdrom:` can be used. If no device specifier is given in the path (e.g. `launcher.elf`), the file is assumed to be a relative path based in the directory Cheat Device was launched from. Loading files from the harddrive (`pfsX:`) is not supported.
* A list of file formats supported by the `databaseReadOnly` and `databaseReadWrite` options can be found [here](https://github.com/root670/CheatDevicePS2/wiki/Cheats).