# Environment Variables

Environment variables contain information about your login session, stored for the system shell to use when executing commands.


Many of these variables are set by default during installation or user creation


It is rare to use environment variables directly, they're referenced by indiviudal applications and daemons as needed.


For example, can see the **HOME** environment variable contents with
```bash
HOME=/home/user
$ echo $HOME
/home/user
```

It is also possible to see all environment variables set with **env** command (_pipe_ the output with **more** for easier readability)

```bash
$ env | more
```

**Environment variables can be useful to:**
- Override default settings
- Manage new settings that the system has no reason to create on its own

For example, when typing a command, the only reason that the computer knows how to find the application for the command is via the **PATH** environment variable, telling it where to look.

The **USER** variable is used by several systems to identify who is requesting a service


Usually the installer program (**apt** on Ubuntu, **brew** on Mac) updates environment variables for a new application.

## Setting an Environment Variable

### Temporary Environment Variables

It is possible to add a location to path, but only works as long as the current shell used to modify the system path remains open

```bash
$ export PATH=$PATH:/home/user/bin
```

If the session is closed, and a new one is opened, the **PATH** variable has reverted to its default state because **PATH** isn't getting set with each new shell.

In order to do that, the variables must be configures to load any time a shell is launched

### Permanent Environment Variables

Set persistent environment variables in the shell configuration file, most common of which is **~/.bashrc**

#### Configuration Files

Bash has a number of [different configuration files](https://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_01.html) to check

![](images/bashstartupfiles.png)

- Bash sources from a different file based on what kind of shell it thinks it is in
	- For an _interactive non-login_ shell it reads ``.bashrc``
	- For an _interactive login_ shell it reads the first of ``.bash_profile``, ``.bash_login``, and ``.profile``.


**~/.bash_profile**
- The preferred configuration file for configuring user environments individually