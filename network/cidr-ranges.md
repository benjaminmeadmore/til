# cidr ranges

Classless Inter-Domain Routing (CIDR) is a compact way to write IP address ranges and their network masks.

In order to connect subnets to an internet gateway, we need to use a route table. And to use a route table, we need to know about CIDR notation. CIDR notation is usefule becuase it lets network engineers allocate address space precisely, aggregate routes and keep routing tables smaller.


## IPv4

An IPv4 address consists of four numbers (octets), separated by dots. Each number is 8 bits. So the number can range from 0 to 255. In the case of a CIDR Range, this IP address is called the CIDR Base IP. 


## the slash

The slash value (e.g. `/24`) shows how many bits belong to the network prefix; the rest identify individual hosts. This is called the CIDR Suffix. `/24` means that of the 32 bits in the IP address, the first 24 bits are fixed. And the remaining 8 can vary from 0 to 255. 

Take the following range: `175.88.0.0/30` 

This is a `/24` suffix, so the first 24 bits are fixed, and the last eight can change. Note that it's convention that the numbers that can change are written as zeros, but you don't need to.

Therefore, the bigger the suffix, the smaller the range. 

## all

And, of course, when using CIDR notation, the last number can be a zero as well: `175.88.0.0/0` 

In practice this means that the all 32 bits are variable and we're talking about all IP addresses here, so the entire internet, or : `0.0.0.0/0` 

## subnet masks 

A subnet mask is a bitmask that encodes the prefix length associated with an IPv4 address: 32 bits, starting with a number of 1-bits equal to the prefix length, ending with 0-bits, and encoded in four-part dotted-decimal format: 255.255.255.0. 

A subnet mask encodes the same information as a prefix length but predates the advent of CIDR. 

[source](https://www.ducktyped.org/p/the-cidr-house-rules)