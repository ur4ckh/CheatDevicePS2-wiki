Each game in the cheat database contains a cheat list, where each cheat contains a list of code lines to be processed by the engine during gameplay. Cheat databases can be stored in the following formats:

1. **Zipped TXT (recommended)** - A zip file containing one or more text files following the format described [below](#txt-cheat-database-format). This can load much quicker than regular text files.

2. **TXT** - A text file that can be edited in a text editor and doesn't need to be converted. This works well for small lists but can take a while to load from memory cards or USB drives if it becomes large. An explanation of the TXT format can be found [below](#txt-cheat-database-format).

The location of the cheat database files need to be set in [CheatDevicePS2.ini](https://github.com/root670/CheatDevicePS2/wiki/Settings).

## Enable Codes
Each game should have a cheat containing an "enable code", AKA a 9-type hook code. These are used to install a jump to the code engine during gameplay to apply the active codes. Some older games don't have 9-type enable codes, in which case the code engine will attempt to find a hook automatically. This has the side-effect of automatically hooking into loader ELFs such as OpenPS2Loader, wLaunchELF, GSM, etc. which has a good chance of causing these loaders to crash. Because of this, it is highly recommended that you add a 9-type enable code to a game's cheat list if it doesn't already have one.

If a cheat contains just 9-type hook codes, it will be automatically enabled when other cheats are enabled in the cheat menu. If a cheat contains 9-type hook codes in addition to regular codes, it can be manually enabled. Some games require the additional code lines to function at all (the Jak and Daxter series, for example), but for other games the additional code lines will corrupt the code engine (as is the case with Metal Gear Solid 3).

The advantage of a 9-type hook code instead of an automatic hook (whether it's using the current method or by hooking directly into the kernel) is that the code engine will apply the codes **only when the game is known to be running** since it does a 32-bit comparison before installing the hook. I had considered using a kernel hook to make Cheat Device universally support all games but couldn't come up with a reliable solution to avoid corrupting loader ELFs.

## TXT Cheat Database Format
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
# Comment line
```
* A **game** is declared as the game's title enclosed by double quotation marks followed by one or more **cheats**.
* A **cheat** begins with a line of text followed by **code lines** formatted as 8 hexidecimal characters for the address, a space character, and 8 hexidecimal characters for the value.
* When two or more cheat titles are placed on adjacent lines without code lines between them, all cheat titles before the last one will be treated as **cheat sections** to organize a cheat list or keep notes to be displayed in the menu.
* A **comment** begins with two forward slashes or a pound sign.
* Only ASCII-encoded text files are supported using either Windows- or Unix-style line endings.

## Button Graphics

You can use special codes to represent gamepad buttons in game and cheat titles that will be replaced with graphics in the menu.

|Button|Code|
|---|---|
|![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonCross.png)|`{CROSS}`|
|![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonCircle.png)|`{CIRCLE}`|
|![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonTriangle.png)|`{TRIANGLE}`|
|![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonSquare.png)|`{SQUARE}`|
|![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonL1.png)|`{L1}`|
|![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonL2.png)|`{L2}`|
|![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonL3.png)|`{L3}`|
|![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonR1.png)|`{R1}`|
|![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonR2.png)|`{R2}`|
|![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonR3.png)|`{R3}`|
|![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonStart.png)|`{START}`|
|![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonSelect.png)|`{SELECT}`|

### Examples

`Hold {L1}+{R1} to Spawn Vehicle`

> Hold ![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonL1.png)+![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonR1.png) to Spawn Vehicle

`Multiple buttons can be placed together {CROSS}{CIRCLE}{TRIANGLE}{SQUARE}{L1}{L2}{R1}{R2}`

> Multiple buttons can be placed together ![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonCross.png)![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonCircle.png)![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonTriangle.png)![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonSquare.png)![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonL1.png)![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonL2.png)![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonR1.png)![](https://raw.githubusercontent.com/root670/CheatDevicePS2/master/resources/buttonR2.png)