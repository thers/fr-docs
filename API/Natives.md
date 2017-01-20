# Incomplete list of natives

## Usage

They're just predefined global LUA methods.

## Methods


### Player

#### `PlayerId(): PlayerId`
Returns current player ID

---

#### `PlayerPedId(): PedId`
Returns current player ped ID
**Use `GetPlayerPed(-1)` instead**

---


### Blips

#### `AddBlipForCoord(x: float, y: float: z: float): BlipId` [UI::ADD_BLIP_FOR_COORD](http://www.dev-c.com/nativedb/func/info/5a039bb0bca604b6)

Adds blip to the coords.

---

#### `SetBlipDisplay(blip: BlipId, displayId: int): void` [UI::SET_BLIP_DISPLAY](http://www.dev-c.com/nativedb/func/info/9029b2f3da924928)

Sets wich display will be used for given blip.

- `displayId == 2` Main map, radar and selectable
- `displayId == 3` Main map, not selectable
- `displayId == 8` Radar

---

#### `SetBlipColour(blip: BlipId, colourId: int): void` [UI::SET_BLIP_COLOUR](http://www.dev-c.com/nativedb/func/info/03d7fb09e75d6b7e)

Sets blip colour. [List of colours](https://github.com/RiderSx/fr-docs/blob/master/Lists/BlipsColours.png)

---

#### `SetBlipRouteColour(blip: BlipId, colourId: int): void` [UI::SET_BLIP_ROUTE_COLOUR](http://www.dev-c.com/nativedb/func/info/837155cd2f63da09)

Sets blip colour. [List of colours](https://github.com/RiderSx/fr-docs/blob/master/Lists/BlipsColours.png)

---

#### `SetBlipSprite(blip: BlipId, sprite: int): void` [UI::SET_BLIP_SPRITE](http://www.dev-c.com/nativedb/func/info/df735600a4696daf)

Sets blip sprite. [List of sprites](https://wiki.gtanet.work/index.php?title=Blips)

---

#### `SetBlipRoute(blip: BlipId, toggle: bool): void` [UI::SET_BLIP_ROUTE](http://www.dev-c.com/nativedb/func/info/4f7d8a9bfb0b43e9)

Toggle path to the blip (like GPS)

---


### Vehicles

#### `CreateVehicle(model: Hash, x: float, y: float, z: float, heading: float, networkHandle: bool, vehicleHandle: bool): VehicleEntity` [VEHICLE::CREATE_VEHICLE](http://www.dev-c.com/nativedb/func/info/af35d0d2583051b0)

Creates vehicle. [Models list](https://wiki.gtanet.work/index.php?title=Vehicle_Models)

> Consider setting both `networkHandle` and `vehicleHandle` to true

---










