[Back](Readme.md)|Natives|[Natives hashes](NativesHashes.md)
---|---|---

---

# Incomplete list of natives


## Usage

They're just predefined global LUA methods.


## Methods

<h1>Common</h1>

### Common

#### `RequestModel(model: Hash): void`
Request to load the given model. Model could be vehicle, ped, weapon or object

---

#### `HasModelLoaded(model: Hash): bool`
Returns `true` if given model has been loaded, `false` otherwise.

> Better check if model loaded before using it

---

#### `HasCollisionForModelLoaded(model: Hash): bool`
Returns `true` if collisions for given has been loaded, `false` otherwise.

> Better check if model loaded before using it

---

#### `GetHashKey(value: string): Hash`
Returns hash key from string name.

> Like for value `NERO` it will return 1034187331

---


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

Sets colour for the path to the blip. [List of colours](https://github.com/RiderSx/fr-docs/blob/master/Lists/BlipsColours.png)

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

#### `GetNumModKits(vehicle: VehicleEntity): int` [VEHICLE::GET_NUM_MOD_KITS](http://www.dev-c.com/nativedb/func/info/33f2e3fe70eaae1d)
Returns number of mod kits for given vehicle.

---

#### `SetVehicleModKit(vehicle: VehicleEntity, modKit: int): void` [VEHICLE::SET_VEHICLE_MOD_KIT](http://www.dev-c.com/nativedb/func/info/1f2aa07f00b3217a)
Sets vehicle mod kit.

> Consider setting the mod kit of the vehicle to `0` if you're gonna apply mods to the vehicle

---

#### `GetVehicleModKit(vehicle: VehicleEntity): int` [VEHICLE::GET_VEHICLE_MOD_KIT](http://www.dev-c.com/nativedb/func/info/6325d1a044ae510d)
Returns vehicle mod kit.

---

#### `GetVehicleWheelType(vehicle: VehicleEntity): int` [VEHICLE::GET_VEHICLE_WHEEL_TYPE](http://www.dev-c.com/nativedb/func/info/b3ed1bfb4be636dc)
Returns wheel type given vehicle has. [List of wheel types](https://github.com/RiderSx/fr-docs/blob/master/Lists/WheelTypes.md)

---

#### `SetVehicleWheelType(vehicle: VehicleEntity, type: int): void` [VEHICLE::SET_VEHICLE_WHEEL_TYPE](http://www.dev-c.com/nativedb/func/info/487eb21cc7295ba1)
Set vehicle wheel type. [List of wheel types](https://github.com/RiderSx/fr-docs/blob/master/Lists/WheelTypes.md)

---

#### `GetNumModColors(p0: int, p1: bool): int` [VEHICLE::GET_NUM_MOD_COLORS](http://www.dev-c.com/nativedb/func/info/a551be18c11a476d)
:no_entry_sign: Returns number of color mods available for vehicle.

> Assuming that `p0` is `VehicleEntity` and `p1` is ???

---

#### `SetVehicleModColor_1(vehicle: VehicleEntity, paintType: int, color: int, 0)` [VEHICLE::SET_VEHICLE_MOD_COLOR_1](http://www.dev-c.com/nativedb/func/info/43feb945ee7f85b8)
Sets vehicle primary color.

- [List of paint types](https://github.com/RiderSx/fr-docs/blob/master/Lists/VehicleColoursTypes.md)
- [List of colours](https://github.com/RiderSx/fr-docs/blob/master/Lists/VehicleColours.md)

---

#### `SetVehicleModColor_2(vehicle: VehicleEntity, paintType: int, color: int)` [VEHICLE::SET_VEHICLE_MOD_COLOR_2](http://www.dev-c.com/nativedb/func/info/816562badfdec83e)
Sets vehicle secondary color.

- [List of paint types](https://github.com/RiderSx/fr-docs/blob/master/Lists/VehicleColoursTypes.md)
- [List of colours](https://github.com/RiderSx/fr-docs/blob/master/Lists/VehicleColours.md)

---

#### `GetVehicleModColor_1(vehicle: VehicleEntity): (paintType: int, color: int)` [VEHICLE::GET_VEHICLE_MOD_COLOR_1](http://www.dev-c.com/nativedb/func/info/e8d65ca700c9a693)
Returns vehicle primary paint type and color.

- [List of paint types](https://github.com/RiderSx/fr-docs/blob/master/Lists/VehicleColoursTypes.md)
- [List of colours](https://github.com/RiderSx/fr-docs/blob/master/Lists/VehicleColours.md)

##### Example of usage:

```lua
local paintType, colour = GetVehicleModColor_1(vehicle)
```

---

#### `GetVehicleModColor_2(vehicle: VehicleEntity): (paintType: int, color: int)` [VEHICLE::GET_VEHICLE_MOD_COLOR_2](http://www.dev-c.com/nativedb/func/info/81592be4e3878728)
Returns vehicle secondary paint type an color.

- [List of paint types](https://github.com/RiderSx/fr-docs/blob/master/Lists/VehicleColoursTypes.md)
- [List of colours](https://github.com/RiderSx/fr-docs/blob/master/Lists/VehicleColours.md)

---


### Weapons

#### `GiveWeaponToPed(ped: *Entity, model: Hash, ammoCount: int, isHidden: bool, equipNow: bool)` [WEAPON::GIVE_WEAPON_TO_PED](http://www.dev-c.com/nativedb/func/info/bf0fd6e56c964fcb)

Gives ped a weapon. [List of weapons](https://wiki.gtanet.work/index.php?title=Weapons_Models)

---
