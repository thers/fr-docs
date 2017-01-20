# Incomplete list of useful natives hashes

## Usage

Call'em with [Citizen.InvokeNative](https://github.com/RiderSx/fr-docs/blob/master/API/Client.md#citizeninvokenativehash-hash-args-any-any)

## List

#### `0x86A652570E5F25DD` [UI:REMOVE_BLIP](http://www.dev-c.com/nativedb/func/info/86a652570e5f25dd)

Removes blip

##### Parameters:

1. `blipPtr: ptr` - Blip pointer to remove

> `blipPtr` needs to be converted using [Citizen.PointerValueIntInitialized](https://github.com/RiderSx/fr-docs/blob/master/API/Client.md#citizenpointervalueintinitializedvalue-int-ptr)

##### Example:

```lua
Citizen.InvokeNative(0x86A652570E5F25DD, Citizen.PointerValueIntInitialized(blip))
```

---
