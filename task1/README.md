# Scripting - task1

## Description

This is a script that writes numbers from 1 -10 in a random order. Each number should appear only once. Script is written in bash.

## Build instruction

Script is cryptographically secure (uses the unix entropy pool data for creation of the random numbers), generates random numbers and does it in a flexible way (from any number to any number span of randoms). It uses the standard *shuf* command of GNU textutils, and the standard unix *random* devices.

## Instalation instruction

Put this script into /usr/bin or your home directory, ensure you have *execute* permission and run:
```
[root@hostname /]# ./script.sh
```

## Usage

Script can serve as a pseudo-random number generator. It generates random numbers within defined scope (in this case 1-10).
There are no command line parameters.

## Known limitations

The script uses */dev/random* as a seed (that is a high quality entropy pool creation, but blocks until the pool is refilled) and it uses the *shuf* command which might not be avialable on all *nix distributions. 
