# Investigating LUA API

## Shared

- `GetPlayerName(id: int)`


## Client

### Global tables

- `exports.[resourceName]` - Resource's public API

### Natives (http://www.dev-c.com/nativedb/ angry-cobra-case)

- `IsControlPressed(0, key: int): bool` - See mappings [here](http://www.dev-c.com/nativedb/func/info/f3a21bcd95725a4a)

- `GetPlayerPed(player: int): NetHandle?` - When player = -1 returns current player's ped?
- `GetPlayerName(id: int): string`
- `GetPlayerWantedLevel(id: int): int?`

- `SetClockTime(hours: int, minutes: int, seconds: int)`
- `PauseClock(toggle: bool)`

- `DoScreenFadeOut(duration: int): void`
- `IsScreenFadingOut(): bool`
- `DoScreenFadeIn(duration: int): void`

### Funcs

- `Citizen.CreateThread(callback: fn(...args)): void` - Creates thread?
- `Citizen.Trace(message: string): void` - Where's the output?
- `[Citizen.]Wait(time: int): void` - Sleep, time in millisends?

- `RegisterNetEvent(name: string): void` - Registers new event name
- `AddEventHandler(name: string, callback: fn(?)): void` - Adds event handler, callback args vary

- `PlayerId(): int` - Returns current player
- `SetTextChatEnabled(toggle: bool): void` - Except obvious?

- `NetworkOverrideClockTime(hours: int, minutes: int, seconds: int): void` - Sets World time? Wut, there's a native for it?!

### NUI a.k.a. NativeUI

Looks like it is kind of system thingie for drawing chat

Discovered `eventName`s:
- `chatResult`

Funcs:

- `RegisterNUICallback(eventName: string, callback: fn(data: ?, cb: fn('ok', ?)) )` - Registers NUI callback, callback arguments seems stable
- `SendNUIMessage({ name?: string, color?: string, message?: string, meta?: string })` - Sends NUI message,used for chat
- `SetNuiFocus(toggle: bool): void` - ???


## Server

### Variables inside event handler

- `source: int` - Player's id

### Funcs

- `GetInstanceId(): number` - What instance ID?

- `GetPlayerEP(id: int): int|string` - Returns player's IP address
- `GetPlayerPing(id: int): int`
- `GetPlayerIdentifiers(id: int): any[]` - retval[1] is GUID

- `SetTimeout(duration: int, callback: fn(...args))`

- `RegisterServerEvent(eventName: string): void` - Registers server event
- `AddEventHandler(eventName: string, callback: fn(...args))` - Registers event handler
- `TriggerEvent(eventName: string, ...args)` - Triggers server(?) event
- `TriggerClientEvent(eventName: string, ...args)` - Triggers client event
- `CancelEvent(): void` - Stops event propagation, must be called inside event handler
- `WasEventCancelled(): bool`

- `RconPrint(message: string): void` - Prints message in server output?
