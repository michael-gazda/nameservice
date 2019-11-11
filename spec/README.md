# Nameservice module specification

## Abstract

This document specifies the nameservice module of the Cosmos SDK.

The nameservice module enables Cosmos-SDK based blockchain to support a naming
system (the mapping of strings to other strings - similar to DNS). Names consist of
the name, value, price and owner stored within a KVStore. The nameservice module is
responsible for allowing users to buy names, delete names and set values to which
the names will resolve. The nameservice module also supports a resolve query to
return the value associated with a name, a whois query to return the price,
value, and owner of a name, and a name query which returns all names stored
within the nameservice store.

Features the module currently supports include:
 - Allow owners to set the value to which a name resolves  
 - Allow users to buy names from current owners
 - Allow users to buy unowned names
 - Delete a name record when requested by the owner
 - Resolve the value of a name in the nameservice
 - Lookup the current value, price and owner of a name
 - Return all names currently stored within the name service
 
## Contents

1. **[Concepts](01_concepts.md)**
2. **[State](02_state.md)**
3. **[Keepers](03_keepers.md)**
4. **[Messages](04_messages.md)**
5. **[Query Types](05_queriers.md)**
6. **[Future Improvements](06_future_improvements.md)**
7. **[Quick Start Guide](Quick_Start_Guide.md)**
