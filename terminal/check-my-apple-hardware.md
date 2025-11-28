# Check your apple system's hardware information

`uname` is a command-line utility that prints basic information about the operating system name and system hardware.

## Useful flags

`uname [OPTIONs]`

```zsh
uname -s, (--kernel-name) # Prints the kernel name.
uname -n, (--nodename) # Prints the system’s node name (hostname). This is the name the system uses when communicating over the network. When used with the -n option, uname produces the same output as the hostname command.
uname -m, (--machine) # Prints the name of the machine’s hardware name.
uname -p, (--processor) # Prints the architecture of the processor.
uname -o, (--operating-system) # Print the name of the operating system. On Linux systems that is “GNU/Linux”
```

When invoked without any options, `uname` prints the kernel name, as if the `-s`option had been specified.

## Output
```zsh
uname -m
```