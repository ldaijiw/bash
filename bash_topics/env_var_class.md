# Environment Variables

- These exist globally on a specific environment or machine
- Generally you don't want to have too many of them
- You can interpolate them into code and other services

## Agenda

- What are variables vs Environment variables in bash
- Process and child process
- Default variables
- How to set environment variables in bash


## Variables in Bash

- Generally use uppercase and assign using no space followed by string or process
```bash
$ MY_VAR=hello
$ echo $MY_VAR
> hello
```

- These variables exist only on the process (current terminal)
- Once you restart the terminal or a new process, these variables no longer exist

## Child Processes

- When terminal runs another file/bash script, it makes a child process 
- A child process is essentially a new terminal, where it executes and then returns to original terminal

### Export

- Can use export to make a variable available to child process
	- In ```my_process.sh```
```
echo "This is a line from my process"

echo $MY_VAR
```

```bash
$ MY_VAR=hello
$ export MY_VAR
$ ./my_process.sh
> This is a line from my process
>
> hello
```

### Checking Variables

- ``printenv``
- ``env``

## Making Variables Persistent in your Computer

- The definitive response lies in understanding how individual terminals are created
- PATH taken
- Each individaul terminal has a path to conclude before opening for you to use it
- To set an environment variable you are going to write in one of the files that it reads as it does its PATH
- In .profile:
```bash
# if running bash
if [ -n "$BASH_VERSION" ]; then
	# include .bashrc if it exists
	if [ -f "$HOME/.bashrc" ]; then
		. "$HOME/.bashrc"
	fi
fi
```

- And can set persistent environment variables in ``.bashrc``



### Bash Variables

To make a variable persistent, add it to Bash PATH

### Bash PATH

A bunch of files it reads in some order

Specific files/locations that the terminal executes and reads before opening and allowing you, the user, or another program to interact with it.

This is a great location to set some variables. These can then be used by child processes

To be used by child process it's useful to ``export`` the variable in the path.

Write variable in .bashrc and .profile, following DRY
- Make .profile look and read .bashrc
- Only have to write variables in .bashrc

**IN PROVISION.sh**
Adding environment variable in provision.sh when setting up vagrant

```
echo "EXPORT DB_HOST=192.168.10.200" >> ~/.bashrc