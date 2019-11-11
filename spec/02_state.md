# State

## Parameters and base types

Names which exist within the nameservice have a single state
in the KVStore. This state is defined by the WhoIs struct:

```
type Whois struct {
	Value string         `json:"value"`
	Owner sdk.AccAddress `json:"owner"`
	Price sdk.Coins      `json:"price"`
}
```
In the case where there is no record for a name, the function
NewWhois can be used to return a Whois struct with the
price set to MinNamePrice:

```
func NewWhois() Whois {
	return Whois{
		Price: MinNamePrice,
	}
}
```

