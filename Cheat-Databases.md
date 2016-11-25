Cheats can be stored in two formats:

1. **CDB (recommended)** - A CDB file can be loaded very quickly and compressed to a small size.

2. **TXT** - These can be edited in a text editor and don't need to be converted. This works well for small lists, but can take longer to load if it becomes too large.

You can use [cdb-util](https://mega.nz/#!LNYB0DAL!n_2Co6zI8c3fun-Mb2-KtA-nIR1wn1vCP_mu4dQR_wg) to convert to/from CDB and TXT formats. The location of the cheat file needs to be set in [CheatDevicePS2.ini](https://github.com/root670/CheatDevicePS2/wiki/Settings).

# Cheat Format
TXT cheat databases follow this format:
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