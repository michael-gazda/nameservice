# State

## Parameters and base types

Names in the nameservice KVStore have a single state
defined by the WhoIs struct parameter set:

```
type Whois struct {
	Value string         `json:"value"`
	Owner sdk.AccAddress `json:"owner"`
	Price sdk.Coins      `json:"price"`
}
```

If a parameter value in the Whois data is modified
a new parameter set is created and the previous one
rendered inactive.

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
