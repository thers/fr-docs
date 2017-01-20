# Incomplete list of useful natives hashes


## Usage

Call'em with [Citizen.InvokeNative](https://github.com/RiderSx/fr-docs/blob/master/API/Client.md#citizeninvokenativehash-hash-args-any-any)


## List

#### `0xB736A491E64A32CF` [ENTITY:SET_ENTITY_AS_NO_LONGER_NEEDED](http://www.dev-c.com/nativedb/func/info/b736a491e64a32cf)

Removes entity

##### Parameters:

1. `entityPtr: ptr` - Entity pointer to remove

> `entityPtr` needs to be converted using [Citizen.PointerValueIntInitialized](https://github.com/RiderSx/fr-docs/blob/master/API/Client.md#citizenpointervalueintinitializedvalue-int-ptr)

##### Example:

```lua
Citizen.InvokeNative(0xB736A491E64A32CF, Citizen.PointerValueIntInitialized(vehicle))
```

---
