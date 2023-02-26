# GREP - G/RE/P (Globally Search for a Regular Expression and Print Matching Lines)

## What is `grep`?

`grep` is a UNIX command, first conceived at Bell Labs, that is given a stream of text as an input along with a regular expression string,
and it outputs only those lines which match said regular expression string. 

## Special Characters for pattern matching

<center>

| Character | Meaning | 
| --- | --- | 
| . | Any single character except NULL or newline | 
| * | Zero or more of the preceding character or expression | 
| [] | Any of the enclosed characters. '-' means character range. `[A-z0-9]` means all alphanumeric characters, `[A-Z]` means all uppercase letters. | 
| ^ | Anchor for beginning of line, or <b>negation</b> of enclosed characters |
| $ | Anchor for End of Line (EOL) |
| \ | Escape special characters which would be eaten up by the shell | 


</center>

## Special characters in ERE (Extended RegEx)

<center>

| Character | Meaning |
| --- | --- |
| {n, m} | Range of occurances of preceding pattern, occuring at least n times and atmost m times | 
| () | Grouping of regular expressions |
| + | One or more of the preceding character / expression | 
| ? | Zero or one of the preceding character / expression |
| \| | Logical OR over the patterns.

</center>

## Character Classes

<center>

| Expression | Class |
| --- | --- |
| [[:print:]] | Printables |
| [[:alpha:]] | Alphabetic |
| [[:alnum:]] | Alphanumeric |
| [[:lower:]] | Lower case characters |
| [[:upper:]] | Upper case characters |
| [[:blank:]] | Space / Tab |
| [[:space:]] | Whitespace |
| [[:punct:]] | Punctuation |
| [[:xdigit:]] | Hexadecimal |
| [[:graph:]] | Non-Space |
| [[:cntrl:]] | Control Characters |

</center>

## Backreferences

`\1` to `\9` are available. A backreference matches the expression given by the `n`th  earlier parathesized expression. 

A line with two occurances of "hello" will be matched by:

`\(hello\).*\1`

## Word Boundary

`\b` denotes the end of a word.

e.g.: `grep -i 'am\b'` would match all words that end with 'am'.

## Square Brackets

Square brackets are used to branch. For example,

`M[ME]` will match 'MM' or 'ME'. 

## Examples

`grep '\bS.*[an]\b` will match all words that start with S and with a or n.

`grep '[aeiou][aeiou]'` will match all lines containing two consecutive vowels.

`grep 'B90[1-4]'` will match all lines containing B901, B902, B903, or B904

The hat character within the square brackets implies _negation_ of the pattern within.

`grep 'B90[^1-4]'` will match all lines NOT containing B901, B902, B903, B904

`grep 'M\{2\}'` will match 'MM'

`grep 'M\{1, 2\}'` will match 'M', 'MM'

`grep '\(ma\).*\1` will match 'ma...ma' like "Umair Ahmad" with matched pattern as "mair Ahma".

`grep '\(a.\).*\1` will match 'a[SOME CHARACTER]...a[SOME CHARACTER]' for instance, it will match the "ankaran" in "Vijay Sankaran" with [SOME CHARACTER] becoming 'n'.

`grep 'M+'` will match sentences with one or multiple occurances of 'M'.

`grep (ma)+` will match sentences with one or multiple occurances of 'ma'.

`grep '^(MD|ED)'` will match all lines starting with MD or ED.

## Example: Parsing the output of dpkg-query using egrep

Consider the following command

<center>

`dpkg-query -W -f'${Section} ${binary:package}\n'`

</center>

This outputs,

<center>

```
admin adduser
libs alsa-topology-conf
libs alsa-ucm-conf
admin apparmor
utils apport
utils apport-symptoms
admin apt
admin apt-utils
admin base-files
admin base-passwd
shells bash
shells bash-completion
math bc
net bind9-dnsutils
net bind9-host
libs bind9-libs:amd64
devel binutils
...
```

</center>

Suppose we want to find commands that are only 4 characters in length, knowing that the command occurs at the end of line, is preceded by a space, we use a pipe to send it to egrep to get:

`dpkg-query -W -f'${Section} ${binary:package}\n' | egrep ' .{4}$'`

</center>


This yields,

<center>

shells bash
utils cpio
admin cron
web curl
shells dash
admin dbus
admin dpkg
utils file
interpreters gawk
utils gpgv
utils grep
utils gzip
utils htop
doc info
metapackages init

</center>


