# Wildcards

- [Wildcards are useful in many ways for a GNU/Linux system](https://tldp.org/LDP/GNU-Linux-Tools-Summary/html/x11655.htm)
- Commands can use wildcards to perform actions on more than one file at a time, or to find part of a phrase in a text file.

# Standard Wildcards (Globbing Patterns)

**Standard wildcards (also known as globbing patterns) are used by various command-line utilites to work with multiple files**

### ?
- Represents any single character
	- ``hd?`` would look for hda, hdb, hdc, etc

### *
- Can represent any number of characters (including zero)
	- ``cd*`` would find cd, cda, cdrom, cdrecord, etc.

### []
- Specifies a range of letters (uses an "or" relationship, only need one to match)
	- ``m[a, o, u]m`` can become mam, mum, mom
	- ``m[a-d]m`` becomes mam, mbm, mcm, mdm

### {}
- Terms are separated by commas and each term must be the name of something or a wildcard
- Wildcard will copy anything that matches either wildcard, or exact names
	- ``cp {*.doc,*.pdf}`` will copy anything ending with .doc or .pdf
	- **Note that spaces are not allowed after the commas**

### [!]
- Similar to [], except that it'll match any character as long as it is not listed between the brackets (logical NOT)
	- rm myfile[!9] will remove all myfiles* but won't remove a file with number 9

### \
- Used as an _escape_ character, i.e. to protect a subsequent special character
	- ``\\`` searches for backslash

## Regular Expressions

**Regular expressions are a type of globbing pattern used when working with text**

They are used for any form of manipulation of multiple parts of text and by various programming languages that work with text

### .
Will match any single character
	- ``m.a`` matches mpa, mea, etc.

### \
- Used as an _escape_ character, i.e. to protect a subsequent special character
	- ``\\`` searches for backslash

### .*
- Used to match any string (equivalent to * in standard wildcards)

### *
- Proceeding item is to be matched zero or more times
	- ``n*`` will match n, nn, nnn, nnnnn, but not na or any other character

### ^
- Means _beginning of the line_
	- ``^a`` means find a line starting with _a_

### $
- Means _end of the line_
	- ``a$`` means find a line ending with _a_

### []
- Specifies a range of letters (uses an "or" relationship, only need one to match)
	- ``m[a, o, u]m`` can become mam, mum, mom
	- ``m[a-d]m`` becomes mam, mbm, mcm, mdm

### |
- Makes a logical OR relationship between wildcards
	- May need to add a backslash before the command to work, because the shell may attempt to interpret this as a pipe

### [^]
- Equivalent to [!] in standard wildcards, performs logical not
	- ``rm myfile[^9]`` will remove all myfiles* but not one with 9 

## Useful categories of characters

- [:upper:] uppercase letters
- [:lower:] lowercase letters
- [:alpha:] alphabetic letters
- [:digit:] numbers in decimal (0 to 9)
- [:alnum:] alphanumeric (alpha + digits)
- [:space:] whitespace meaning spaces, tabs, newlines, and similar
- [:graph:] graphically printable characters excluding space
- [:print:] printable characters including space
- [:punct:] punctuation characters meaning graphical characters minus alpha/digits
- [:cntrl:] control characters meaning non-printable characters
- [:xdigit:] characters that are hexadecimal digits