# SYSTEM COMMANDS

## Basic Commands

<center>

| Command | Explanation |
| --- | --- |
| pwd |  Show current working directory, short form of 'present working directory' (pwd). |
| ls | Lists all files in current directory. Add `-s` option to show the file sizes beside each file. |
| ls -l | Lists all files in current directory along with file permissions. |
| ls -l &lt;dir&gt; | Lists all the contents of the directory specified (and not the present working directory). |
| ls -i | Lists all files with their inode. |
| ls -a | List all files along with _hidden_ files as well as '.' and '..'. |
| ls -ld &lt;dir&gt; | Lists only the given file / directory and its associated permissions. |
| ls -R &lt;dir&gt; | Recursively traverse the given directory |
| cd &lt;dir&gt; | Change to a directory. |
| whoami | Prints your username. |
| mkdir &lt;directory name&gt; | Creates new directory |
| rm &lt;file&gt; | Removes a file or directory. Use the "-r" command to be recursive and remove all files in that directory, and "-f" command to force. `rm -rf <file / directory>` can be dangerous! |
| alias &lt;your command&gt;="some combination"  | Sets `<your command>` as an alias (aka substitute) for the combination.  For example, the command "rm" takes a switch "-i" which prompts before every removal. So if you wanted to be warned before deletion of every file, you'd use `rm -i <your files>`. If you are a beginner, it is useful to have this enabled by default, because you might end up executing an `rm` that you didn't want to, so it gives you another chance to correct the error by prompting you to press `y` (to continue) or `n` (to stop). So you would do,<br> `alias rm="rm -i"` <br> Now, whenever executing `rm`, the shell will always interpret it as `rm -i`. This will only last for the current session. To set it permanently, you'll have to modify your `.bashrc` file. (more on this later). Without any argument `alias` will output the aliases configured for the shell. |
| unalias &lt;alias to remove&gt; | To remove an alias use `unalias <alias to remove>` |
| touch &lt;file name 1&gt; &lt;file name 2&gt; ... | Updates the timestamp of the given files. If files do not exist, an empty file(s) is/are created. This can be used as a way to create a file that does not exist. |
| man &lt;command&gt; | Opens the _UNIX manual pager_ for the given command. If you want to know what a command does, and what options it takes, you may use this, e.g. `man rm` will give you all the information regarding the `rm` command. |
| file &lt;filename&gt; | Outputs the characteristics of the given file, usually the file format and its associated information. |
| chmod &lt;permissions&lt; &lt;filename&gt; | Modifies the permissions of the file. |
| groups | Show which groups the user belongs to. (A user itself is a group, so at least 1 group exists) |
| less &lt;file&gt; | Shows a text file as pages to be read in sections split in a way to fit on the screen. |
| head &lt;file&gt; | Outputs the _first_ 10 lines of the file by default. Use the `-n <lines>` switch to specify more or less than 10. |
| tail &lt;file&gt; | Outputs the _last_ 10 lines of the file by default. Use the `-n <lines>` switch to specify more or less than 10. | 
| wc &lt;file&gt; | Outputs the number of newlines, words and bytes in a file.<br>e.g.,<br> `> wc hello.txt`<br>`27 98 581 hello.txt`<br> Here we now know that `hello.txt` has 27 lines, 98 words, and is 581 bytes in size.| 
| which &lt;command&gt; | Tells you the location of the executable corresponding to that command. | 
| apropos &lt;search term&gt; | Lists the commands containing the given search term in the man pages. Equivalent to `man -k`. |
| info | Opens the home page of the Linux manpages in the terminal. | 
| type &lt;command&gt; | Tells you what type of command it is, whether the command is stored as an executable or a shell builtin or an alias. |
| cp &lt;src&gt; &lt;dest&gt; | Copies the source file to the destination. If destination is a file that exists, it prmopts the user if they wish to overwrite said file if executed with "-i". Use `-r` to be recursive and copy all the  directories and files within a directory as well. |
| mv &lt;src&gt; &lt;dest&gt; | Moves the source file to the destination. If destination is a file that exists, it prmopts the user if they wish to overwrite said file if executed with "-i". Use `-r` to be recursive and move all the  directories and files within a directory as well. |
| stat &lt;file&gt; | Gives the information on what is the size of the file, along with how many blocks it occupies on the file system. |
| du &lt;file&gt; | This gives what is the size of the file on the file system. For example, if a file system has a minimum block size of 4096 bytes, then a file name with the size 4553 bytes will actually occupy 8096 bytes (next multiple of 4096). You cannot store fractional blocks on a hard disk. So `stat` will tell you the file size is 4.5K while `du` will tell you it is `8.0K`. |
| echo &lt;expression&gt; | Equivalent to `print` in Python or `printf` in C, it essentially outputs the expression on to the screen. If you want to print a variable, prefix a `$` sign in front of the variable name to print it out. If you want to have multiple spaces in your string, enclose your string in `"` or `'` characters. If you want to give multiline input, you can leave on quotation mark open and press ENTER, the shell will continue asking for input until it encounters a terminating quotation mark.<br> <b>Note</b>: `echo $USERNAME` and `echo "$USERNAME"` will both output your username, however, `echo '$USERNAME'` will output `$USERNAME` instead. Another way to unescape the "$" sign is by prefixing a `\$`.<br> e.g.: <br> `>echo "hostname is $HOSTNAME and username is $USERNAME"`<br>`hostname is sgautam-laptop and username is sgautam`<br> `>echo "hostname is \$HOSTNAME and username is $USERNAME"`<br>`hostname is $HOSTNAME and username is sgautam` | 
| printenv | Prints all the environment variables for the current user. If given an argument (a variable name), then it prints the value of that variable. |
| ps | Show all processes running. `ps -e` shows all processing running on the operating system. `/sbin/init` (the initialization program) is assigned a PID of 1. The Linux kernel has a PID of 0. `ps -f` shows the parent process IDs (PPID) of the processes running. |
| coproc &lt;command&gt; &lt;args&gt; | Execute a command with given arugments without losing control of the shell. |  
| bc | The command line calculator. Consider the following: <br> `echo "3+4*(5/4)" \| bc` <br>, this outputs the value of 7 (note that operator precedence doesn't work in bc). |
| lsb_release -a | Show Linux distribution information |
| uname -a | Show Linux kernel and architecture information |
| md5sum file1.txt | Generate a file with a name that is the MD5 checksum of the contents of file1.txt |
| sha1sum file1.txt | Generate a file with a name that is the SHA-1 (160 bit) checksum of the contents of file1.txt |
| sha256sum file.txt | Generate a file with a name that is the SHA-256 (256-bit) checksum of the contents of file1.txt | 

</center>

## File Permissions

Let's execute the command `ls -l` in some directory, we get an output like this:

```
sgautam@sgautam-laptop:/mnt/c/Users/sgaut/OneDrive/Documents$ ls -l

-r-xr-xr-x 1 sgautam sgautam     172 Jan  3 19:00  CALCULUS3.url
-r-xr-xr-x 1 sgautam sgautam     172 Sep  8 16:24  CEM.url
-rwxrwxrwx 1 sgautam sgautam   25167 Jan 24 18:20  CV-SGAUTAM.docx
-rwxrwxrwx 1 sgautam sgautam   38316 Jan 24 18:25  CV-SGAUTAM.pdf
drwxrwxrwx 1 sgautam sgautam    4096 Jan 13 17:05  ClothSimulator
drwxrwxrwx 1 sgautam sgautam    4096 Jan  9 21:58 'Custom Office Templates'
drwxrwxrwx 1 sgautam sgautam    4096 Jan 25 19:19  GHProjects
```

The first column with the weird letters that go "-rwxrw-r--" and so on is what is called the _permissions_
of the file.

The following image makes this meaning clearer:

<center>

![](permissions.png)

</center>

### Taking and granting permissions

Suppose we want to grant write permissions to the group specified by the file. We write:

`chmod g+w <file>`

This command specifies `g` for the group setting, `+` meaning we want to *grant* permission, and `w` standing for write permission.

Suppose we want to take away executable permissions to all others who are not the owner or the group, we write:

`chmod o-x <file>`

The `o` stands for others, and `-` standing for "take away" and `x` for eXecutable permissions. 

**Idea**: This can be useful if you are running a kiosk and don't want users to be able to open up the terminal, you simply take away the executable permissions of the terminal application from all others except the `root` user. 

### The type attribute

We have not described the first character of the permissions string, which is the _type_ attribute. Essentially it tells you want *kind* of file or directory it is.

<center>

| Type | Description |
| --- | --- |
| `-` | Good old **File** |
| `d` | **Directory** (A 'folder' for Windows users) |
| `l` | A **Symbolic Link**. It is a structure in the filesystem that points to another file. |
| `c` | A **Character File**. In UNIX philosophy, [everything is a file](https://en.wikipedia.org/wiki/Everything_is_a_file). Including your screen! Your terminal display for example is a character file. When you "write" to this file, instead of the output going to the hard disk or SSD drive, it goes into the terminal buffer and then is rendered to the screen. |
| `b` | A **Block File**. Block files are chunks of data that can be read into memory when requested by an application. |
| `s` | A **Socket File**. If you know C programming, you'll know that sockets are used for IPC (interprocess communication). This socket file can be used to send or take in data to and from a program. Other programs can also write to a program's socket file to send data to the target probem. |
| `p` | A **Named Pipe**. A pipe is basically an output buffer of a program. We can only read from a pipe. |

</center>

For now, you'll just have to keep in mind that if the first character of the permissions string is anything except a `-` (file) and `d` (directory), you'll have to be careful and not do something you're not supposed to, as messing with special file types can break applications or even the OS.

## Links

Think of links as file system structures that point to the same chunk of file data. A _hard link_ is a link that has the same inode (a UNIX file system structure that is essentially a "pointer" in the hard disk space to a file) as the original file. A _symbolic link_ is a file that points to another file.

To create a hard link, simply use:

`ln <file> <hard link name>`

To create a symbolic link use:

`ln -s <file> <symbolic link name>`

## In memory file systems `/proc` and `/sys`

Adhering to UNIX's "everything is a file philosophy", even the processes are represented in a file system structure in Linux. One can read these files (they are read only) to see information regarding processes. They are also used by processes to do interprocess communication.

e.g., reading `/proc/cpuinfo` will give a program / user CPU information. This is useful, as for x86/x64 platforms one has to use the `cpuid` instruction to figure out CPU information and every other architecture (like ARM or RPi) will have their own ways of getting CPU information, and therefore a program can easily figure out the CPU characteristics without using such architecture specific implementations and simply reading `/proc/cpuinfo`.

## Shell Variables, Exit Codes

Shell variables are variables that can be set, unset, and used in part of an expression just like variables in other programming languages are. Shell variables are prefixed with a `$` sign. Some common shell variables include:

<center>

| Shell Variable | Information |
| --- | --- | 
| `$USERNAME` | User name of the user use to log in to the session. Use `whoami` or `$USER` for the current user. |
| `$HOME` | Home directory of the current user | 
| `$PWD` | Present working directory |
| `$HOSTNAME` | Host name of the current user |
| `$PATH` | List of all directories to search for when a command is entered to look for the command |
| `$0` | Name of the shell |
| `$$` | Process ID (yes, the process id you use in C/C++) of the shell |
| `$?` | Return code of the previous program |
| `$-` | Flags set in bash shell |

</center>

Print variables using `echo $<variable name>`.

Exit codes are a programs return value. C/C++ programmers might be familiar that their programs `main` function as the prototype `int main(void)` or `int main(int argc, char** argv)`. The `return 0;` (usually) from main is what describes your exit code. We return 0 from main for most programs because it indicates successful execution. Any other value is considered a failure of some sort, however, some return values are reserved by the Linux kernel. 

<center>

| Return value | Status |
| --- | --- |
| `0` | Success / OK |
| `1` | Failed | 
| `2` | Misuse | 
| `126` | Command cannot be executed |
| `127` | Command not found |
| `130` | Process killed by sending SIGINT signal (usually Ctrl + C) |
| `137` | Process killed by `kill -9 <pid>` |

</center>

## Variables

### Declaring Variables

1. Variable names must not start with a number.
2. Alphanumeric and underscore characters are allowed.
3. The value can be a number, string or command.
4. No spaces around the "=" sign (bash is case-sensitive).

### Restricting variable types

- `declare -i myvar`: Restrict `myvar` to integer only.

- `declare -l myvar`: Restrict `myvar` to lower case characters only.

- `declare -u myvar`: Restrict `myvar` to upper case characters only.

- `declare -r myvar`: Makes `myvar` read only.

### Removing restrictions

- `declare +i myvar`: Unrestrict.

- `declare +l myvar`: Unrestrict.

- `declare +u myvar`: Unrestrict.

- `declare +r myvar`: Does not work, once variable becomes read only, it is read only.

### Set variable to output of a command

`` myvar=`date` ``

`myvar` is now set to the output of the `date` command at that specific point in time. An hour later, `date` will output a different time, but the value in `myvar` will not change.


<center>

| Action | Bash |
| --- | --- |
| Setting a variable | `myvar="something"` |
| Removing a variable | `unset myvar` |
| Getting a variable value ($ prefix) | `echo $myvar` <br> `echo ${myvar}_something` <br> Note: Its generally good practice to enclose variable names around curly braces. |
| Set a variables default value (if variable does not exist) | `myvar:="default"` |
| Use a variables default value (if variable does not exist) | `myvar:-"default"` |
| Reset to a variables default value (if variable is set) | `myvar:+"default"` |
| Test if a variable is set | `[[ -v  $myvar ]]` <br> `echo $?` <br> 1 if set, 0 if not set. |
| Length of a string variable | `echo ${#myvar}` |
| Splice a string | `echo ${myvar:5:4}` <br> Read as: skip first 5 characters of string in `myvar` and output the next 4 characters. | 
| Remove first matching pattern | `echo ${myvar#pattern}` |
| Remove maximum matching patterns | `echo ${myvar##pattern}` |
| Keep first matching pattern | `echo ${myvar%pattern}` |
| Keep maximum matching patterns | `echo ${myvar%%pattern}` |
|  First char to upper case | `echo ${myvar^}` |
| Full string to upper case | `echo ${myvar^^}` <br> In case of lower case replace `^` with `,`. |

</center>

## UNIX directories

The following are some of the standard UNIX directories and their meanings.

<center>

| Directory | What It is |
| --- | --- |
| / | Root, the top of the file system hierarchy | 
| /bin | Contains the executables of the various installed programs. Most shell commands, along with your GCC compiler are located here. |
| /dev | Adhering to UNIX's "everything is file" principle, this is a directory containing system device files. While they might appear as files, they are actually a way to interact with the various devices connected to the system in a standard file I/O way. |
| /etc | System configuration files. |
| /home | The /home directory contains subdirectories with the name of the user. The personal files for every user is in its respectively named subdirectory. For example, if sgautam and gcsharma are two users using the same computer, their personal files would be ideally in /home/sgautam and /home/gcsharma |
| /mnt | This contains the mountpoint of various temporary file systems. One can mount a CDROM to /mnt/cdrom, and going there one would see all the files inside that CD-ROM, or you could also mount a hard drive, which usually looks like /mnt/4f310b-2331f5-12ac3f-b6890/ (device ID), you could also mount a ISO file and access it like a file system. | 
| /opt | This stands for 'optional', it contains various files from third party sources such as various device vendors, or additional software installed after OS installation. | 
| /sbin | This contains administrative programs. Some examples as fdisk (use to partition the hard disk), fsck (use to check for disk errors) etc. |
| /usr | This directory contains user-related files. This is typically read-only. |
| /var | This contains files that vary over time, usually system log files, mail system files, spooling files, etc. |
| /dev/null | A sink. Anything piped to /dev/null is discarded. Used for when you don't want to show errors, or log output to the screen or file, and you instead pipe it to /dev/null/. |

</center>

## Combinations of Commands

<center>

| Combination | Explanation
| --- | --- | 
| command1 && command2 | command2 is executed if and only if command1 succeeds | 
| command1 \|\| command2 | command2 is executed if and only if command1 fails |
| command1; command2 | command1 and command2 are executed | 
| command1 &gt; file1 | Create a new file named 'file1' and redirect stdout of command1 to file1 |
| command1 &gt;&gt; file1 | Append the stdout of command1 to file1 |
| command1 2&gt; file1 | Create a new file named 'file1' and redirect stderr of command1 to file1 |
| command1 2&gt;&amp;1 | Redirect stderr to stdout |  
| command1 | command2 | Pipe the output of command1 to command2. stdout of command1 is stdin of command2 | 

</center>