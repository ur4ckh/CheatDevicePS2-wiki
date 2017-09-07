Each game in the cheat database contains a cheat list, where each cheat contains a list of code lines to be processed by the engine during gameplay. Cheat databases can be stored in two formats:

1. **CDB (recommended)** - A CDB file can be loaded very quickly and compressed to a small size.

2. **TXT** - A TXT file can be edited in a text editor and doesn't need to be converted. This works well for small lists but can take a while to load if it becomes too large.

You can use [cdb-util](https://github.com/root670/cdb-util/releases) to convert to/from CDB and TXT formats. The location of the cheat file needs to be set in [CheatDevicePS2.ini](https://github.com/root670/CheatDevicePS2/wiki/Settings).

# TXT Cheat Database Format
```
"Game Name"
Enable
90000000 88888888

Cheat 1
27654321 12345678

Cheat 2
12345678 98765432

Cheat Section
Cheat 3
11111111 00000000

Cheat 4
20000004 00000001
20000008 00000001

// Comment line
```
* A **game** is declared as the game's title enclosed by quotation marks followed by one or more cheats.
* A **cheat** begins with a line of text followed by **code lines** formatted as 8 hexidecimal characters for the address, a space character, and 8 hexidecimal characters for the value.
* When two or more cheat titles are placed on adjacent lines without code lines between them, all cheat titles before the last one will be treated as **cheat sections** to organize a cheat list or keep notes to be displayed.
* A **comment** begins with double slashes.