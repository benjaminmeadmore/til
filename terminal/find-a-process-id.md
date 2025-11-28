# ps aux & grep 

## ps
The `ps` command, which stands for `process status`, is the easiest way to find what processes are running on your machine. It works by reading the virtual files in /proc and doesn't need privileges to run. Also included is each process' `pid` (_process id_), which may be used as a parameter in various function calls, allowing processes to be manipulated, such as adjusting the process's priority or killing it altogether.

### Usage
`ps [-e -A] [-f -F] [u] [a] [x] [-u -U] [-N -deselect] [-y] [-l]`

```zsh
ps -ef # See every process on the system in full format;
ps -ely # See every process on the system in long format with no flags;
ps aux # List all processes on the systen in user (BSD) format;
ps -U root -u root u # To see every process running as root (real & effective ID) in user format.
```

### Zombies 
Processes marked <defunct> are dead processes (so-called "zombies") that remain because their parent has not destroyed them properly.  These processes will be destroyed by  _init_(8) if the parent process exits. You can get both the `pid` and the parent `pid` of a process by including the `-f` flag with `ps`.

## grep 
The `grep` command is the fastest way to find what a process that's running on your machine actually is. 

### Usage 
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

## Useful flags
`traceroute [-n] [-w wait_time] [-i initial_ttl] [-m max_ttl] [-p dest_port] [-q nqueries] [-t tos] host [data_size]`

## Detail
- You are generally menat to get anywhere in the world in under 20hops. 
- To interrupt just type `ctrl+c`
- The traceroute command uses the TTL field in the IP header to cause routers and servers to generate specific return messages. It then determines the address of the first hop by examining the source address field of the ICMP time-exceeded message.