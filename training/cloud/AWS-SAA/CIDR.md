# Classless Inter-Domain Routing - CIDR

## Overview

CIDR (Classless Inter-Domain Routing) is a method for allocating IP addresses and routing IP packets on the internet. It replaces the older class-based system (Class A, B, C) with a more flexible approach using prefix lengths. It is primarily used for IPv4 IP addresses.

* IPv4 addresses are 32-bit numbers that are typically represented as four decimal octets separated by dots. Each octet is a number from 0 to 254 representing one byte of the IP address.
* CIDR notation is of the format: IP/Prefix
  * The IP portion is the base address of the block. Usually this is an IP where the host bits will all be zero.
  * The prefix length is a value from 0 - 32 and specifies the number of network bits.
  * The remaining portion of the bits are used to represent individual hosts.
  * A subnet mask is derived from the prefix where the first n bits are set to 1.
  
## Calculating Number of Hosts

The following formula can be usesd to calculate the number of hosts for a CIDR block. Assuming that $n$ is the CIDR prefix length and $H_T$ is the resulting number of hosts.

```math
H_T=2^{(32-n)}
```

This will return the count of all IP addresses in the range, including the network and broadcast addresses. To calculate the total number of usable hosts ($H_U$) use the following formula.

```math
H_U=2^{(32-n)}
```

Note that blocks `/31` and `/32` have special rules and cannot be calculated using the two formulas above.

| Prefix | Number of Hosts |
|-------:|-----------------|
| /31    | 2               |
| /32    | 1               |

## Calculating Start and End IPs

There are two approaches that can be used to calculate the start and end IP addresses for a CIDR block. Note that the `/0` prefix is special and covers all IP addresses.

### Using Binary

1. Convert the IP address into binary format.
2. The first `n` bits represent the network prefix and should not be modified.
3. To calculate the start IP (network address) set all of the host bits to `0`.
4. To calculate the end IP (broadcast address) set all of the host bits to `1`.
5. Convert thje binary number back to decimal.

### Without Binary

1. The start IP ($I_S$) will usually be the given IP address (assuming it is the network address).
2. The end IP ($I_E$) can be calculated with the following formula.

```math
I_E=I_S + 2^{(32-n)} - 1
```
