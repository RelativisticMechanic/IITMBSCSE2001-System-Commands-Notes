# Debian Package Manager (DEB)

## Basic Package Management

<center>

| Command | What It Does |
| --- | --- |
| apt-cache search &lt;keyword&gt; | Search for 'keyword' in package cache |
| apt-cache pkgnames | Show installed packages |
| apt-cache pkgnames &lt;keyword&gt; | Show packages matching 'keyword' | 
| apt-cache show &lt;package name&gt; | Show package information usually name, section, version, architecture, priority, MD5, SHA1, SHA2 checksum etc. |

</center>

## Installing, Modifying and Removing Packages

* Only sudoers can install, modify and remove packages. 

<center>

| Command | What It Does |
| --- | --- |
| sudo apt-get update | Synchronize the local package cache with the repositories |
| sudo apt-get upgrade | Upgrade all packages |
| sudo apt-get install &lt;package&gt; | Install the package |
| sudo apt-get reinstall &lt;package&gt; | Install the package |
| sudo apt-get autoremove | Remove packages installed as a dependency of some other package but no longer needed |
| sudo apt-get clean | Remove all retrieved package files |
| sudo apt-get remove &lt;package&lt; | Remove a package |
| sudo apt-get purge &lt;package&lt; | Remove package and all associated files with it | 

</center>

## Exploring the installed packages

* `/var/lib/dpkg` is the directory which contains information regarding the installed packages.
* `cat /var/lib/dpkg/arch` will tell you the architectures for which packages have been installed. On a normal x86-64 PC, this will usually be `amd64` and `i386`.

## Using dpkg

<center>

| Command | What It Does |
| --- | --- | 
| dpkg -l pattern | List all packages that match pattern |
| dpkg -L package | List all files part of said package |
| dpkg -s package | Report status of package |
| dpkg -S pattern | Search installed packages for file matching pattern |

</center>

Install a .deb package which you downloaded from the internet using:

`sudo dpkg -i &lt;path_to_deb.deb&gt;`
