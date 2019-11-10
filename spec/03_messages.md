# Messages

### MsgSetName

MsgSetName defines a SetName message

```
type MsgSetName struct {
	Name  string         `json:"name"`
	Value string         `json:"value"`
	Owner sdk.AccAddress `json:"owner"`
}
```

### MsgBuyName

MsgBuyName defines the BuyName message

```
type MsgBuyName struct {
	Name  string         `json:"name"`
	Bid   sdk.Coins      `json:"bid"`
	Buyer sdk.AccAddress `json:"buyer"`
}
```

### MsgDeleteName

MsgDeleteName defines a DeleteName message

```
type MsgDeleteName struct {
	Name  string         `json:"name"`
	Owner sdk.AccAddress `json:"owner"`
}
```
