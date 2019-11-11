# Messages

### Setting the value for a name

`MsgSetName` allows the owner of a name to set the
return value for that name when it is resolved. 

```
type MsgSetName struct {
	Name  string         `json:"name"`
	Value string         `json:"value"`
	Owner sdk.AccAddress `json:"owner"`
}
```

MsgSetName has three attributes needed to set the value for a name:

 - name: The name trying to be set.
 - value: What the name resolves to.
 - owner: The owner of that name.

### Buy a name

`MsgBuyName` allows the purchase of a
name either from an existing owner or if not owned.

```
type MsgBuyName struct {
	Name  string         `json:"name"`
	Bid   sdk.Coins      `json:"bid"`
	Buyer sdk.AccAddress `json:"buyer"`
}
```

MsgBuyName has the three attributes needed to set the value for a name:

 - name: The name trying to be set.
 - bid: The amount bid for the name.
 - buyer: The buyer of the name.

If the name is not owned, the MinPrice is burned and the buyer
is awarded the name. If the name is owned, and the submitted bid
is higher than the price of the name, the buyer is awarded the name.

MsgBuyName contains validation which ensures:
 - The buyer currently has enough coin for the transaction.
 - The bid is high enough to purchase the name.

### Delete a name

MsgDeleteName allows the deletion of a name.

```
type MsgDeleteName struct {
	Name  string         `json:"name"`
	Owner sdk.AccAddress `json:"owner"`
}
```

MsgDeleteName requires two attributes:
 - name: The name trying to be deleted.
 - owner: The owner of that name.
