# LUA API Investigation

## Types

- `*Entity: int` - Entity ID
- `*Model: int` - Model ID
- `VehicleSeat: int` - -1 for driver, [0,] for passangers
- `PlayerId: int` - Player ID
- `PlayerServerId: int` - Player ID on server
- `PedId: int` - Ped ID
- `PedType: int` - [Ped type](PedTypes.md)
- `KillReason: int` - [Kill reason](KillReasons.md)
- `Hash: int64?`

## Shared

### Funcs

- `GetPlayerName(id: int)`


## Client

### Events

- `onPlayerDied fn(playerId: PlayerId, reason: int, position: vec3)`
- `onPlayerKilled fn(playerId: PlayerId, attackerId: PlayerId, reason: int, position: vec3)`

### Global tables

- `exports.[resourceName]` - Resource's public API

### Natives (http://www.dev-c.com/nativedb/ angry-cobra-case)

- `DoesEntityExist(entity: *Entity): bool`

- `IsControlPressed(0, key: int): bool` - See mapping [here](http://www.dev-c.com/nativedb/func/info/f3a21bcd95725a4a)

- `GetPlayerPed(playerId: PlayerId): PedId` - When player = -1 returns current player's ped? See `Client:Funcs:PlayerPedId()`
- `GetPlayerName(playerId: PlayerId): string`
- `GetPlayerWantedLevel(playerId: PlayerId): int?`
- `IsPlayerDead(playerId: PlayerId): bool`

- `GetVehiclePedIsUsing(pedId: PedId, currentVehicle: bool = true): VehicleEntity` - if `currentVehicle = false` then will return last used `VehicleEntity`
- `GetEntityModel(entity: *Entity): *Model`
- `GetDisplayNameFromVehicleModel(vehicleModel: *Model): string`
- `IsPedInAnyVehicle(pedId: PedId, atGetIn: bool): bool` - Read more about `atGetIn` [here](http://www.dev-c.com/nativedb/func/info/997abd671d25ca0b)
- `GetPedInVehicleSeat(vehicleEntity: VehicleEntity, seat: VehicleSeat): PedId`
- `GetVehicleMaxNumberOfPassangers(vehicleEntity: VehicleEntity): int` - [0,]
- `GetVehiclePedIsTryingToEnter(pedId: PedId): VehicleEntity`
- `GetSeatPedIsTryingToEnter(pedId: PedId)`

- `SetClockTime(hours: int, minutes: int, seconds: int)`
- `PauseClock(toggle: bool)`

- `DoScreenFadeOut(duration: int): void`
- `IsScreenFadingOut(): bool`
- `DoScreenFadeIn(duration: int): void`

### Natives hashes

They must be called using `Citizen.CallNative(hash, ...args)`.

- `0xB736A491E64A32CF (entity: EntityPointerValue)` - Marks entity as no longer needed, engine will delete it

### Funcs

- `Citizen.CreateThread(callback: fn(...args)): void` - Creates thread?
- `Citizen.Trace(message: string): void` - Where's the output?
- `[Citizen.]Wait(time: int): void` - Sleep, time in millisends?

- `Citizen.InvokeNative(hash: Hash, ...args: any): any`
- `Citizen.PointerValueIntInitialized(ptr: int): ptrVal`
- `Citizen.PointerValueFloatInitialized(ptr: float): ptrVal`
- `Citizen.PointerValueInt(ptr: int): ptrVal`
- `Citizen.PointerValueFloat(ptr: float): ptrVal`
- `Citizen.PointerValueVector(ptr: vec) ptrVal`
- `Citizen.ReturnResultAnyway`
- `Citizen.ResultAsInteger`
- `Citizen.ResultAsFloat`
- `Citizen.ResultAsString`
- `Citizen.ResultAsVector`

- `RegisterNetEvent(eventName: string): void` - Registers new event name
- `AddEventHandler(eventName: string, callback: fn(?)): void` - Adds event handler, callback args vary

- `PlayerId(): PlayerId` - Returns current player ID
- `PlayerPedId(): PedId` - Returns current player ped ID
- `GetPlayerServerId(playerId: PlayerId): PlayerServerId`

- `SetTextChatEnabled(toggle: bool): void` - Except obvious?

- `NetworkOverrideClockTime(hours: int, minutes: int, seconds: int): void` - Sets World time? Wut, there's a native for it?!

- `echo(message: string): void` - ?

### NUI a.k.a. NativeUI

`eventName`:
- `chatResult`

Funcs:

- `RegisterNUICallback(eventName: string, callback: fn(data: ?, cb: fn('ok', ?)) )` - Registers NUI callback, callback arguments seems stable
- `SendNUIMessage({ name?: string, color?: string, message?: string, meta?: string })` - Sends NUI message,used for chat
- `SetNuiFocus(toggle: bool): void` - ???


## Server

### Events

- `baseevents:onPlayerDied fn(killedByPed: PedType, ...)`
- `baseevents:onPlayerKilled fn(killedByPlayerId: PlayerId, ...)`
- `baseevents:onPlayerWasted fn(pos: vec3)`
- `baseevents:enteringVehicle fn(vehicle: VehicleEntity, seat: vehicleSeat, vehicleDisplayName: string)`
- `baseevents:enteringAborted`
- `baseevents:enteredVehicle fn(vehicle: VehicleEntity, seat: vehicleSeat, vehicleDisplayName: string)`
- `baseevents:leftVehicle fn(vehicle: VehicleEntity, seat: vehicleSeat, vehicleDisplayName: string)`

### Variables inside event handler

- `source: PlayerId` - Source player id

### Funcs

- `GetInstanceId(): int` - What instance ID?

- `GetPlayerByServerId(playerServerId: PlayerServerId): {name: string}`
- `GetPlayerEP(playerId: PlayerId): int|string` - Returns player's IP address
- `GetPlayerPing(playerId: PlayerId): int`
- `GetPlayerIdentifiers(playerId: PlayerId): any[]` - retval[1] is GUID
- `GetPlayerGuid(playerId: PlayerId): int|string` - Player's GUID, noice

- `DropPlayer(playerId: PlayerId, message: string): void`
- `TempBanPlayer(playerId: PlayerId, message: string): void`

- `SetTimeout(duration: int, callback: fn(...args))`

- `RegisterServerEvent(eventName: string): void` - Registers server event
- `AddEventHandler(eventName: string, callback: fn(...args))` - Registers event handler
- `TriggerEvent(eventName: string, ...args)` - Triggers server(?) event
- `TriggerClientEvent(eventName: string, ...args)` - Triggers client event
- `CancelEvent(): void` - Stops event propagation, must be called inside event handler
- `WasEventCancelled(): bool`

- `RconPrint(message: string): void` - Prints message in server output?



# The fucks

- `[Client] AddUIHandler(eventName: string, callback: fn(data: any, cb: fn())): void` - And then query `http://{resourceName}/{eventName}` `HTTP GET`
- `[Client] PollUI()` - unclear

