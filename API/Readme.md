[Client](Client.md)|[Server](Client.md)
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
- `VehicleSeat: int` - -1 for driver, [0,] for passangers
- `PlayerId: int`
- `PlayerServerId: int`
- `PedId: int`
- `PedType: int`
- `KillReason: int`
- `Hash: int64`

## References

- [Server API](Server.md)
- [Client API](Client.md)
