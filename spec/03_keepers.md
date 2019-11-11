# The Keeper

The Keeper maintains the link to storage and exposes getter/setter methods for
the various parts of the state machine. The nameservice module has a single
keeper which connects the nameservice to the bank, codec and types modules.

## Keeper Struct

```
type Keeper struct {
	CoinKeeper bank.Keeper
	storeKey sdk.StoreKey
	cdc *codec.Codec
}
```
`bank.Keeper` - This is a reference to the Keeper from the bank module.
`*codec.Codec` - This is a pointer to the codec that is used to encode and decode binary structs.
`sdk.StoreKey` - This is a store key which gates access to a sdk.KVStore which persists the state of the application.

## Getters and Setters

`GetWhoIs` returns the WhoIs data for a name.  
```
GetWhois(ctx sdk.Context, name string) types.Whois {
	store := ctx.KVStore(k.storeKey)
	if !k.IsNamePresent(ctx, name) {
		return types.NewWhois()
	}
	bz := store.Get([]byte(name))
	var whois types.Whois
	k.cdc.MustUnmarshalBinaryBare(bz, &whois)
	return whois
}
```
`SetWhoIs` sets the WhoIs data for a name
```
SetWhois(ctx sdk.Context, name string, whois types.Whois) {
	if whois.Owner.Empty() {
		return
	}
	store := ctx.KVStore(k.storeKey)
	store.Set([]byte(name), k.cdc.MustMarshalBinaryBare(whois))
}
```

`DeleteWhois` deletes the WhoIs data for a name
```
DeleteWhois(ctx sdk.Context, name string) {
	store := ctx.KVStore(k.storeKey)
	store.Delete([]byte(name))
}
```

`ResolveName` returns the value a name resolves to
```
ResolveName(ctx sdk.Context, name string) string {
	return k.GetWhois(ctx, name).Value
}
```

`SetName` sets the value that a name resolves to
```
SetName(ctx sdk.Context, name string, value string) {
	whois := k.GetWhois(ctx, name)
	whois.Value = value
	k.SetWhois(ctx, name, whois)
}
```

`HasOwner` returns whether a name has an owner
```
HasOwner(ctx sdk.Context, name string) bool {
	return !k.GetWhois(ctx, name).Owner.Empty()
}
```

`GetOwner` returns the current owner of a name
```
GetOwner(ctx sdk.Context, name string) sdk.AccAddress {
	return k.GetWhois(ctx, name).Owner
}
```

`SetOwner` sets the current owner of a name
```
SetOwner(ctx sdk.Context, name string, owner sdk.AccAddress) {
	whois := k.GetWhois(ctx, name)
	whois.Owner = owner
	k.SetWhois(ctx, name, whois)
}
```

`GetPrice` returns the current price of a name
```
GetPrice(ctx sdk.Context, name string) sdk.Coins {
	return k.GetWhois(ctx, name).Price
}
```

`SetPrice` sets the current price of a name
```
SetPrice(ctx sdk.Context, name string, price sdk.Coins) {
	whois := k.GetWhois(ctx, name)
	whois.Price = price
	k.SetWhois(ctx, name, whois)
}
```

`GetNamesIterator` returns an iterator where the name is the key
and the values are the corresponding WhoIs struct
```
GetNamesIterator(ctx sdk.Context) sdk.Iterator {
	store := ctx.KVStore(k.storeKey)
	return sdk.KVStorePrefixIterator(store, nil)
}
```

`IsNamePresent` returns whether the name exists in the store
```
IsNamePresent(ctx sdk.Context, name string) bool {
	store := ctx.KVStore(k.storeKey)
	return store.Has([]byte(name))
}
```
