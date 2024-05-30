unspendable
====================

The script generates a valid base58 encoded address string that meets the validation checks for most cryptocurrency networks but is generated in such a way that the private key can never be found. This is useful for generating a coin burn address where any coins sent to the address can never be recovered. Using this method also allows injecting a vanity keyword into the address so that the address visibly looks much less like a random address and more like the burn address it is meant to be.

USAGE:
----------------------------

Simply call the python script and pass in the cryptocurrency's address prefix and a vanity keyword that will appear directly after the prefix. For example, to generate a burn address for the Regus network you can use the following:

```
$ ./unspendable.py G burnaddress
Result: GburnaddressXXXXXXXXXXXXXXXXaVHd6h
Decimal Address Prefix: 38
```

The first argument of **G** is the address prefix for the Regus network.  
The 2nd argument of **burnaddress** is the vanity keyword to insert.

**NOTE:** Only certain alphanumeric characters are valid for the address prefix and vanity keyword. The list of valid characters are: **123456789ABCDEFGHJKLMNPQRSTUVWXYZabcdefghijkmnopqrstuvwxyz**

The actual address is **GburnaddressXXXXXXXXXXXXXXXXaVHd6h** and as an added check, the decimal address prefix of **38** is also displayed to eliminate guessing. The decimal address prefix must match the 2nd bit in the **PUBKEY_ADDRESS** of the coin's source code or else the address will not be valid. [Click here to view the PUBKEY_ADDRESS for Regus mainnet](https://github.com/RegusCrypto/Regus/blob/v27.0/src/kernel/chainparams.cpp#L128). If you are not able to generate a valid address for your network it is most likely because the decimal address prefix doesn't match. You may have to change the vanity keyword to something that starts with a different number or letter to find one that matches your network's decimal address prefix. [Click here for more information about how the address prefixes work](https://en.bitcoin.it/wiki/List_of_address_prefixes).

