# Incomplete list of natives

## Usage

They're just predefined global LUA methods.

## Methods


### Player

#### `PlayerId(): int`

Returns native player id

---


### Blips

#### `AddBlipForCoord(x: float, y: float: z: float): BlipId` [UI::ADD_BLIP_FOR_COORD](http://www.dev-c.com/nativedb/func/info/5a039bb0bca604b6)

:no_entry_sign: Adds blip to the coords.

---

#### `SetBlipDisplay(blip: BlipId, displayId: int): void` [UI::SET_BLIP_DISPLAY](http://www.dev-c.com/nativedb/func/info/9029b2f3da924928)

:no_entry_sign: Sets wich display will be used for given blip.

- `displayId == 2` Main map, radar and selectable
- `displayId == 3` Main map, not selectable
- `displayId == 8` Radar

---

#### `SetBlipColour(blip: BlipId, colourId: int): void` [UI::SET_BLIP_COLOUR](http://www.dev-c.com/nativedb/func/info/03d7fb09e75d6b7e)

:no_entry_sign: Sets blip colour. [List of colours](https://github.com/RiderSx/fr-docs/blob/master/Lists/BlipsColours.png)

---
