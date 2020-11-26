# Bash

## Files in Linux

- Everything is a file
	- Linux is not concerned with file extensions, they will maintain whatever format they were in
- Find type of file with
```bash
file <filename>
```
- File names are case sensitive, and using spaces in names can be problematic and require a backslash as an escape character
```bash
mkdir "my documents"

cd my\ documents/
```

**TO OPEN MANUAL PAGE FOR A COMMAND TO SEE AVAILABLE OPTIONS**
```bash
man <command>
```

## Environment Variables

Environment variables contain information about your login session, stored for the system shell to use when executing commands.

Many of these variabels are set by default during installation or user creation

## Head, Tail, Sort

- head and tail default 10
- head -n3 sample.txt (prints first 3 lines)
- tail -n3 sample.txt (prints last 3 lines)
- sort sample.txt (sorts in alphabetical order)
- sort -r sample.txt (sorts in reverse order)


## Permissions

- There are 3 levels of permissions
	- User
	- Group
	- Other

Check permissions with ``ll``

- Execute is 1
- Write is 2
- Read is 4

Can combine to make a maximum of 7
- You can also use add/remove permissions using alias
	- r (read)
	- w (write)
	- x (executable)

Can change permissions with ``chmod``

### Root User

- Is superuser, can escalate privileges using ``sudo``
- Can make user ``sudo users`` list in system to make other users super users


## Streams

- ``STDIN``: Standard input of a command
- ``STDOUT``: Standard output or the result of a command
- ``STDERR``: Standard error is the output error of a commands


## Redirects

Ability to capture STDOUT of a program and redirect it into a file

- head -n3 sample.txt > newfile.txt
	- Creates new file/replaces anything in file (Truncates)
- head -n3 sample.txt >> newfile.txt
	- Adds 3 lines to end of file, without replacing (Appends)
	- Can add a 2 before a redirect to ensure the redirect captures the STDERR
		- ``ls filename.txt 2>> error_logs.txt`` will capture any error and redirect it
	- Alternatively can add 1 to capture STDOUT
	- Can capture both with ``2>&1``

## Wildcards

- Wildcards are useful in many ways for a GNU/Linux system
- Commands can use wildcards to perform actions on more than one file at a time, or to find part of a phrase in a text file.



## Piping

- Using **|** can feed ouput from left command as input to right command
- ``ls | head -n3`` output the first 3 files/dirs from ls


## Grep

**G**lobal **R**egular **E**xpression **P**rint

- Used to serach for strings/text from a file or from output of another command
	- returns lines where it finds a match


## Process Management

- ``ps`` shows all processes currently running
	- ``PID`` is process ID
	- Can find specific processes by piping with grep
		-``ps aux | grep vagrant``
- ``kill <PID>`` to kill the process

- ``&`` runs in background and shows PID e.g. ``vagrant up &``

