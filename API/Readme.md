[Client](Client.md)|[Server](Server.md)
---|---

---

# LUA API Reference

All of this was found in many of the places like official forums, users resources and server resources.

Some of it was tested.

## Legend

Whenever you see :no_entry_sign: near item you should consider it untested (except natives, it's too much of them to test each one).

## Types aliases

Just to make it easier to understand what is what there are type aliases.
Scheme: `TypeAliasName: actualType`.

Also there're so called pattern-type-aliases: `*Entity: int` means that every type alias which name ends with `Entity` should be considered the same type alias. `VehicleEntity` is `*Entity` also.

- `*Entity: int`
- `*Model: int`
- `VehicleSeat: int` - -1 for driver, 0,1,2,... for passangers
- `PlayerId: int`
- `PlayerServerId: int`
- `PedId: int`
- `PedType: int`
- `KillReason: int`
- `Hash: int64`
- `BlipId: int`

## Declarations explained

Types that used here:
- `int` - 32 bits Integer
- `int64` - 64 bits Integer
- `bool` - Boolean
- `float` - Float
- `string` - String
- `{keyName = valueType, key2Name = value2Type}` - Hash table
- `{keyType => valueType}` - Map
- `ptr` - Pointer
- `type[]` - array of `type`
- `fn(arg: argType): returnValueType` - Anonymous function
- `void` - Void
- `any` - Unknown variable type
- `type1|type2` - Variable can be `type1` **or** `type2`

For variables: `varName: varType`.

For methods: `methondName(arg1: arg1Type, arg2: arg2Type): returnValueType`.

## References

- [Server API](Server.md)
- [Client API](Client.md)
- [Natives](Natives.md)
- [Natives hashes](NativesHashes.md)
