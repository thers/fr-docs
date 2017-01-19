|[Back](Readme.md)|Client|[Server](Server.md)|
|---|---|---|
---


# Client side LUA API


## Events

Event Name|Callback declaration
----------|--------------------
:no_entry_sign:`onPlayerSpawn`|`fn()`
:no_entry_sign:`onPlayerDied`|`fn(playerId: PlayerId, reason: int, position: float[3])`
:no_entry_sign:`onPlayerKilled`|`fn(playerId: PlayerId, attackerId: PlayerId, reason: int, position: float[3])`


## Methods

#### `GetInstanceId(): int`
:no_entry_sign: What instance ID?

---


#### `Citizen.CreateThread(callback: fn()): void`
Creates new thread for `callback` function

---

#### `Citizen.Trace(message: string): void`
Prints message to scripts logs (Can be accessed pressing F8)

--

#### `[Citizen.]Wait(time: int): void`
:no_entry_sign: Sleep time in milliseconds (1/1000 of a second)

---

#### `Citizen.InvokeNative(hash: Hash, ...args: any): any`
Invokes Native

---

#### `Citizen.PointerValueIntInitialized(value: int): ptr`
Returns pointer intialized by `value`

---

#### `Citizen.PointerValueFloatInitialized(value: float): ptr`
Returns pointer initialized by `value`

---

#### `Citizen.PointerValueInt(): ptr`
Returns initialized int pointer

---

#### `Citizen.PointerValueFloat(): ptr`
Returns initialized float pointer

---

#### `Citizen.PointerValueVector(): ptr`
Returns intialized vector pointer

---

#### `Citizen.ReturnResultAnyway(): ptr?`
Returns flag to pass as last argument of `Citizen.InvokeNative`, if native returns something, pass it

---

#### `Citizen.ResultAsInteger(): ptr?`
Returns pointer of int to pass to native that will write data to it, but it will be returned from `Citizen.InvokeNative`

---

#### `Citizen.ResultAsFloat(): ptr?`
Returns pointer of int to pass to native that will write data to it, but it will be returned from `Citizen.InvokeNative`

---

#### `Citizen.ResultAsString(): ptr?`
Returns pointer of int to pass to native that will write data to it, but it will be returned from `Citizen.InvokeNative`

---

#### `Citizen.ResultAsVector(): ptr?`
Returns pointer of int to pass to native that will write data to it, but it will be returned from `Citizen.InvokeNative`

---

#### `RegisterNetEvent(eventName: string): void`
Registers new event name

---

#### `AddEventHandler(eventName: string, callback: fn(...args: any[])): void`
Adds event handler, callback args vary

---

#### `PlayerId(): PlayerId`
Returns current player ID

---

#### `PlayerPedId(): PedId`
Returns current player ped ID

---

#### `GetPlayerServerId(playerId: PlayerId): PlayerServerId`
Returns player's server ID by it's ID

---

#### `SetTextChatEnabled(toggle: bool): void`
:no_entry_sign: Toggles displaying of native chat

---

#### `NetworkOverrideClockTime(hours: int, minutes: int, seconds: int): void`
Sets World time
