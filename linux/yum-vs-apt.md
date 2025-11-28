# yum vs apt

`yum`, short for Yellowdog Updater Modified, is commonly used in Red Hat-based distributions like CentOS and RHEL. On the other hand, `apt`, which stands for Advanced Packaging Tool, is widely used in Debian, Ubuntu, and their derivatives

## Commands
Both support the most commonly used cmds such as update, upgrade, install, remove, etc..
```bash
$ sudo yum update -y 
$ sudo apt update -y 
```
## Configs file locations
- apt organizes options into functional groups and stores them in the `/etc/apt/apt.conf` file, which is organized in a tree structure

- yum allows options to be set with global and repository-specific effects, and the configuration is managed in the `/etc/yum.conf` file, which consists of two sections