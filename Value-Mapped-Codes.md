*Note: This feature is being worked on in the `variable-codetype` branch. When it's ready, it'll be merged to `master`.*

A value-mapped cheat allows a cheat to reference a list of possible values without duplicating the cheat for each value. For example, a game's inventory system might use an array of bytes to represent the contents of each slot, where the slot's value represents a unique item. Rather than creating separate cheats for each combination of slot and item, a single cheat can be defined for each slot using a reference to a value map with each item's digits. In Cheat Device, choosing the *Slot X* cheat displays a list of item descriptions, allowing any item's digits to be used with the cheat.

A value map is defined by a name enclosed by brackets followed by value-key pairs separated by a `` ` ``, `=`, or `-` character. Values are in hexidecimal and can be either 2, 4, or 8 characters in length. A game can define one or more value maps that can be referenced by any cheat that appears after it's defined. The address of a cheat's code line can be associated with a value map by using a `$` character followed by the value map's name instead of the usual value digits that would follow the address.

## Example

```
"Grand Theft Auto Vice City v1.40"

[Car]
82=Landstalker
83=Idaho
84=Stinger
85=Linerunner
86=Perennial
87=Sentinel
88=Patriot (Boat)

Press {SELECT} to Spawn a Car
10275F8C 0000001A
10275F9C 00000042
20275FB0 0C09E528
00275FB4 $Car
10275FB6 00002404
```

* A value map named `Car` with 7 entries is defined for `Grand Theft Auto Vice City v1.40`.
* A cheat named `Press {SELECT} to Spawn a Car` references the map in the 4th code line. When the cheat is chosen in Cheat Device, a list of all possible `Car` values to be used with the cheat is displayed.
* If *Stinger* is chosen from the list, for example, `00275FB4 00000084` will be added to the list of codes to be processed by the code engine.

## Notes

* Value map names cannot contain spaces.
* Up to 16 value maps per game can be defined.
* It doesn't matter when a value map is defined as long as no cheats reference it before it is defined.
* Different games can have value maps with the same name.
* Value map entries are insensitive to whitespace around the separating character.