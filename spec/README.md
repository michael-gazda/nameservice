# Nameservice module specification

## Abstract

This document specifies the nameservice module of the Cosmos SDK.

The nameservice module enables Cosmos-SDK based blockchain to support a naming
system (the mapping of strings to other strings similar to DNS). Names consist of
the name, value, price and owner stored within a KVStore. The nameservice module is
responsible for allowing users to buy names, delete names and set values to which
the names will resolve. The nameservice module also supports a resolve query to
return the value associated with a name, a whois query to return the price,
value, and owner of a name, and a name query which returns all names stored
within the nameservice store.

## Contents

1. **[Concepts](01_concepts.md)**
2. **[State](02_state.md)**
3. **[Messages](03_messages.md)**
4. **[Queriers](04_queriers.md)**
