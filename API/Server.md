|[Back](Readme.md)|[Client](Client.md)|Server|
|---|---|---|

---

# Server side Lua API

## Events

Event Name|Callback declaration
----------|--------------------
:no_entry_sign:`baseevents:onPlayerDied`   |`fn(killedByPed: PedType, ...args)`
:no_entry_sign:`baseevents:onPlayerKilled` |`fn(killedByPlayerId: PlayerId, ...args)`
:no_entry_sign:`baseevents:onPlayerWasted` |`fn(pos: vec3)`
:no_entry_sign:`baseevents:enteringVehicle`|`fn(vehicle: VehicleEntity, seat: vehicleSeat, vehicleDisplayName: string)`
:no_entry_sign:`baseevents:enteringAborted`|`fn()`
:no_entry_sign:`baseevents:enteredVehicle` |`fn(vehicle: VehicleEntity, seat: vehicleSeat, vehicleDisplayName: string)`
:no_entry_sign:`baseevents:leftVehicle`    |`fn(vehicle: VehicleEntity, seat: vehicleSeat, vehicleDisplayName: string)`


## Methods

#### `GetInstanceId(): int`
:no_entry_sign: What instance ID?

---

#### `GetPlayerName(playerId: PlayerId): string`
:no_entry_sign: Returns player's name

---

#### `GetPlayerByServerId(playerServerId: PlayerServerId): {name: string}`
:no_entry_sign: Returns actual player ID by it's server ID

---

#### `GetPlayerEP(playerId: PlayerId): int|string`
:no_entry_sign: Returns player's IP address

---

#### `GetPlayerPing(playerId: PlayerId): int`
:no_entry_sign: Returns player ping in milliseconds

---

#### `GetPlayerIdentifiers(playerId: PlayerId): any[]`
:no_entry_sign: retval[1] is player's GUID

---

#### `GetPlayerGuid(playerId: PlayerId): int|string`
:no_entry_sign: Returns player's GUID

---

#### `DropPlayer(playerId: PlayerId, message: string): void`
:no_entry_sign: Unclear

---

#### `TempBanPlayer(playerId: PlayerId, message: string): void`
:no_entry_sign: Unclear

---

#### `SetTimeout(time: int, callback: fn(...args)): void`
:no_entry_sign: When `time` will be exceeded will invoke `callback`

---

#### `RegisterServerEvent(eventName: string): void`
Registers server event

---

#### `AddEventHandler(eventName: string, callback: fn(...args))`
Registers event handler

---

#### `TriggerEvent(eventName: string, ...args)`
Triggers server event

---

#### `TriggerClientEvent(eventName: string, ...args)`
Triggers client event

---

#### `CancelEvent(): void`
Stops event propagation, must be called inside event handler

---

#### `WasEventCancelled(): bool`
Whether or not event has been canceled, must be called inside event handler

---

#### `RconPrint(message: string): void`
:no_entry_sign: Prints message in server output?
