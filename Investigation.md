# Investigating LUA API

## Types

- `*Entity: int` - Entity ID
- `*Model: int` - Model ID
- `VehicleSeat: int` - -1 for driver, [0,) for passangers
- `PlayerId: int` - Player ID
- `PedId: int` - Ped ID

## Shared

### Funcs

- `GetPlayerName(id: int)`


## Client

### Global tables

- `exports.[resourceName]` - Resource's public API

### Natives (http://www.dev-c.com/nativedb/ angry-cobra-case)

- `IsControlPressed(0, key: int): bool` - See mappings [here](http://www.dev-c.com/nativedb/func/info/f3a21bcd95725a4a)

- `GetPlayerPed(playerId: PlayerId): int` - When player = -1 returns current player's ped?
- `GetPlayerName(playerId: PlayerId): string`
- `GetPlayerWantedLevel(playerId: PlayerId): int?`

- `GetVehiclePedIsUsing(pedId: PedId, currentVehicle: bool = true): VehicleEntity` - if `currentVehicle = false` then will return last used `VehicleEntity`
- `GetEntityModel(entity: *Entity): *Model`
- `GetDisplayNameFromVehicleModel(vehicleModel: *Model): string`

- `SetClockTime(hours: int, minutes: int, seconds: int)`
- `PauseClock(toggle: bool)`

- `DoScreenFadeOut(duration: int): void`
- `IsScreenFadingOut(): bool`
- `DoScreenFadeIn(duration: int): void`

### Funcs

- `Citizen.CreateThread(callback: fn(...args)): void` - Creates thread?
- `Citizen.Trace(message: string): void` - Where's the output?
- `[Citizen.]Wait(time: int): void` - Sleep, time in millisends?

- `RegisterNetEvent(eventName: string): void` - Registers new event name
- `AddEventHandler(eventName: string, callback: fn(?)): void` - Adds event handler, callback args vary

- `PlayerId(): PlayerId` - Returns current player
- `SetTextChatEnabled(toggle: bool): void` - Except obvious?

- `NetworkOverrideClockTime(hours: int, minutes: int, seconds: int): void` - Sets World time? Wut, there's a native for it?!

### NUI a.k.a. NativeUI

`eventName`:
- `chatResult`

Funcs:

- `RegisterNUICallback(eventName: string, callback: fn(data: ?, cb: fn('ok', ?)) )` - Registers NUI callback, callback arguments seems stable
- `SendNUIMessage({ name?: string, color?: string, message?: string, meta?: string })` - Sends NUI message,used for chat
- `SetNuiFocus(toggle: bool): void` - ???


## Server

### Events

- `baseevents:onPlayerDied fn(killedByPlayerId: PlayerId, pos: vector3)`
- `baseevents:onPlayerKilled fn(killedBySomethingType: int, pos: vector3)`
- `baseevents:onPlayerWasted`
- `baseevents:enteringVehicle fn(vehicle: VehicleEntity, seat: vehicleSeat, vehicleDisplayName: string)`
- `baseevents:enteringAborted`
- `baseevents:enteredVehicle fn(vehicle: VehicleEntity, seat: vehicleSeat, vehicleDisplayName: string)`
- `baseevents:leftVehicle fn(vehicle: VehicleEntity, seat: vehicleSeat, vehicleDisplayName: string)`

### Variables inside event handler

- `source: PlayerId` - Source player id

### Funcs

- `GetInstanceId(): int` - What instance ID?

- `GetPlayerEP(playerId: PlayerId): int|string` - Returns player's IP address
- `GetPlayerPing(playerId: PlayerId): int`
- `GetPlayerIdentifiers(playerId: int): any[]` - retval[1] is GUID

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
