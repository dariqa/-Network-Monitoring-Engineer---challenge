# -Network-Monitoring-Engineer---challenge
## Take home challenge recruitment process - Task 1

### Description

This is a script that writes numbers from 1 -10 in a random order. Each number should appear only once. Script is written in bash.

### Build instruction

Script is cryptographically secure (uses the unix entropy pool data for creation of the random numbers), generates random numbers and does it in a flexible way (from any number to any number span of randoms). It uses the standard *shuf* command of GNU textutils, and the standard unix *urandom* and/or *random* devices.

### Instalation instruction

Put this script into /usr/bin or your home directory and run
```
[root@hostname /]# ./script.sh
```

### Usage

Script can serve as a pseudo-random number generator. It generates random numbers within defined scope (in this case 1-10).
There are no command line parameters.

### Known limitations

Reads from *urandom* do not block, but are not so random. When read during early boot time, */dev/urandom* may return data prior to the entropy  pool  being  initialized.so it is to be avoided.
*random* is high quality entropy pool only creation, but blocks until the pool is refilled (in case we want many randoms).
