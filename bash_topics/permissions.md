# Permissions

## File Permissions

- In Linux/Unix, everything is a file
- All files on a system have permissions that allow/prevent others from viewing, modifying, or executing.
- The super user "root" has the ability to access any file on the system, and to change any files owned by root, **sudo** must be used
- Each file has access restrictions with permissions, user restrictions with owner/group association.
- Permissions are referred to as bits

There are 3 types of **Access Restrictions**

| Permission | Action | chmod Option |
|:--------: |:----: |:----------: |
| Read | View | r or 4 |
| Write | Edit | w or 2 |
| Execute | Execute | x or 1 |

There are also 3 types of **User Restrictions**

| User | Is Output |
|:-: |:-: |
| Owner | -rwx------|
| Group | ----rwx---|
| Other | -------rwx|

**NOTE**: The restriction type scope is not inheritable, i.e. the file owner will be unaffected by restrictions set for his group or everybody else

## Folder/Directory Permissions

| Permission | Action | chmod Option |
|:--------: |:----: |:----------: |
| Read | View contents, i.e. ``ls`` command | r or 4 |
| Write | Create or remove files from dir | w or 2 |
| Execute | ``cd`` into directory | x or 1 |

**NOTE**: Write access for a directory allows deleting of files in the directory even if the user does not have write permissions for the file

## Viewing and Changing Permmissions

### Viewing Permissions

View permissions with (e.g.)
```bash
$ ll

-rw-r--r--  1 root root 288 2005-11-13 19:24 /etc/hosts
```
This shows the file "/etc/hosts" whic is owned by user root and belongs to root group

The permissions are as follows
```
-rw-r--r--
owner = Read & Write
group = Read
other = Read
```

### Changing Permissions

Command to use to modify permissions is ``chmod``. There are two ways to modify permissions
- Numbers
- Letters (which are easier to understand)

Usage:
```bash
chmod <options> <filename>
```
| Options | Definition |
| :-----: | :--------: |
| u | owner |
| g | group |
| o | other |
| a | all (same as ugo) |
| x | execute |
| w | write |
| r | read |
| + | add permission |
| - | remove permission |
| = | set permission |

