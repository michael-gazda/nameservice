# Concepts

## nameservice

The `nameservice` module:

The nameservice module was designed to:
 - Allow users to buy names from current owners
 - Allow users to buy names which are not owned
 - Allow owners to set the value to which a name resolves  
 - Resolve the value of a name in the nameservice
 - Lookup the value, price and owner of a name
 - Return all names stored within the name service

Name ownership is determined as follows:
 - The owner of a given name will be the current highest bidder.
 - When a name is purchased the new owner shall pay the previous owner a bid amount higher than the previous owner paid.
 - If a name is not owned the buyer must burn a MinPrice amount to aquire the name. 
 