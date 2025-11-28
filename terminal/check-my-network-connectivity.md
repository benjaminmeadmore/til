# Traceroute

`traceroute` is a cli utility which will show you all hops involved from IP-to-IP when travelling from your device to any accessible host on the web. 

## Utility
`traceroute <host>` without any options will send three 40-byte ICMP datagrams with an initial TTL of 1, a maximum TTL of 30, a timeout period of 5 seconds, and a TOS specification of 0 to destination UDP port number 33434. 

## Usage
```zsh
traceroute 8.8.8.8 # Run cmd
traceroute to 8.8.8.8 (8.8.8.8), 64 hops max, 40 byte packets
 1  10.0.16.1 (10.0.16.1)  28.251 ms  3.228 ms  3.075 ms
 2  * * *
 3  * * *
 4  72.14.214.70 (72.14.214.70)  13.618 ms
    167.98.17.75 (167.98.17.75)  8.126 ms  5.016 ms
 5  192.178.97.191 (192.178.97.191)  6.267 ms *
    192.178.97.117 (192.178.97.117)  14.661 ms
 6  142.250.215.127 (142.250.215.127)  5.505 ms
    dns.google (8.8.8.8)  5.593 ms  5.741 ms
```
_8.8.8.8 is Google's DNS IP so is a good destination host server for testing_ 

## Pre-requisites
- ICMP outbound traffic needs to be enabled on your device and port 33434 needs to be open

## Useful flags
`traceroute [-n] [-w wait_time] [-i initial_ttl] [-m max_ttl] [-p dest_port] [-q nqueries] [-t tos] host [data_size]`

## Detail
- You are generally ment to get anywhere in the world in under 20hops. 
- To interrupt just type `ctrl+c`
- The traceroute command uses the TTL field in the IP header to cause routers and servers to generate specific return messages. It then determines the address of the first hop by examining the source address field of the ICMP time-exceeded message.