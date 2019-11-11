# Concepts

## nameservice

The `nameservice` module:

There are three concepts within the nameservice module:
 - Storing name value data
 - Managing the buying and ownership of names
 - Querying existing name information from the Store

### Storing name value data

The most basic goal of a name service is to map human readable names with
less readable values. The most common example of a name service is DNS
(Domain Name System) which maps readable domain names like `example.com`
with an IP Address such as `93.184.216.34`. The concept is similar with
the nameservice module. A name is purchased, and the owner then sets a
value to which it will resolve.

### Buying and selling names

The nameservice module provides functionality to allow the
purchasing of names which are either unowned or from the current
owner. Name ownership is determined as follows:
 - The owner of a given name is the current highest bidder.
 - When buying a name the new owner will pay the previous owner a bid amount higher than the previous owner paid.
 - If a name is not owned, the buyer must burn a MinPrice amount to aquire the name. 
 - The current owner of a name may elect to relinquish ownership by deleting it from the Store.
 
### Querying information from the Store

The nameservice provides three queries for obtaining existing data from the Store.
 - Resolve: This allows the retrival of a value when a name is submitted.
 - WhoIs: The price, value, and owner of the name are returned.
 - Name: Returns all names currently in the Store.
