# Bash

Get drangerous in bash.

## What is Bash?

Simply put, Bash is a Unix shell that allows you to enter commands and write programs (know as bash scripts). It's widely used as it ships as the defauly login shell for most versions of Linux and MacOS since Mojave. There's even an Windows version.

Bash is short for "Borne-again shell" a tounge-in-cheek reference to the shell it replaced: the Borne shell (sometime stylized as `sh`). It's more formally known as GNU Bash.

Many alternatives to Bash exist, like ZShell or fish; however, their different implmentations means their scripts are incompatable. For exmaple, Bash uses logical operators like `! && ||` while in fish they're written as `not and or`.

## `.bash_profile`, `.bashrc`, and `.profile`

These are initlization files (scripts) that are run when bash is invoked. They may set variables or add something to you `$PATH`. While file is run depends how bash is invoked (e.g., login, purely interactive, ect.).

### `.bash_profile` - Login shells

`.bash_profile`: gets executed for login shell. OS X is unique in that it logs in everytime you open a new instance of the terminal.

Commands that will invoke a login shell:

```
sudo su -
bash --login
ssh user@root
```

When bash is invoked as a login shell, these files are executed in order:

1. `/etc/profile`
2. `~/.bash_profile`
3. `~/.bash_login`
4. `~/.profile`

### `.bashrc` - Interactive shells (no login)

`.bashrc`: gets exected for non login, but still interative shells. It's also executed when you run `/bin/bash`.

Commands that will invoke a purely interavtive shell:

```
sudo su
bash
ssh user@host /path/to/command
```

Non-interactive shells

Shells that do not automatically execute any scripts like `~/.bashrc`.

```

```

## Common Bash Commands

### ls

**`ls -l` output**

The `-l` flag indicates a list in long format.

```

\$ ls -l

-rw-r--r-- 1 wyatt staff 721 May 2 19:46 bash.md
^ ^ ^ ^ ^ ^ ^
A B C D E F G

```

Key:

- A: File permissions
- B: Links
- C: Owner
- D: Group
- E: File size
- F: Date
- G: File name

A. File Permissions

```

-rw-r--r--
FUUUGGGOOOS

```

F = File type flag (will appear as `d` if it's a directory)
U = User/owner
G = Group members
O = All others
S = Alternative access (null if blank)

**B. Link Count**

What constitutes a link here varies.

**C. Owner Account**

**D. Group**

**E. File size**

Again, depends on the filesystem. In OSX, it refers to bytes. Use `ls -lah` for human readable file sizes.

**F. Date**

## Bash concepts

Input/Output redirection

- `<`: redirect contents of file to the program
- `>`: takes STDOUT of specified program and writes it to a given file. If the file exists, the contents are overwritten.
- `>>`: takes STDOUT of specified program and adds it to a given file. If the files exists, the redirect is appended to the contents of the file.
- `|`: takes output of given program and redirects it as input to another program. This process is known as piping. (`ls | grep "2004"` is a good example, using `ls` and `grep` to find files with a matching Regex pattern.)

## Installing a package from a binary

Downloading a binary from the internet using curl

`curl -LO https://site.com/dowload/linux-amd64.tar.gz`
The `-L` flag tells curl to retry at a new address if it recieves a redirect response.
The `-O` flag tells curl to write the downloaded file to be save to a local location of the same name.

Untarring a tarball

The `tar` command can compress and extract files. It was originally used to for magnetic tapes, hence it's name Tape ARchive. GZip is the most used scheme for compressing `.tar` files. If you file ends in `.tar.gz`, it was compressed using GZip.

```bash
tar -xvf tarball.tar.gz
tar -xvfz tarball.tar.gz # uncompress
tar -xvf tarball.tar.gz -C /usr/local/bin # output contents to directory
```

```bash
tar -xvf
```

### What package to choose?

When installing some software that needs some manual work over the command line, you'll likely see packages that look look something like this:

`helm-v3.0.0-beta.3-darwin-amd64.tar.gz`

Let's break this down a little bit.

`helm-v3.0.0-beta.3` refers to the package we want to download: the 3rd beta release of Helm. In our case, we want to download a prerelease version of Helm 3 to test and play around with. If you're looking for the latest stable version, the word "beta" should tip you off that you're looking for the wrong version.

`darwin-amd64` refers to machines running a 64-bit version of Mac OSX.

`.tar.gz` tells us how the package. While probably wouldn't pick a pacakge based on this information, you could

Below are some definitions to decifer the names and choose the package right for you.

**Operating systems**

- darwin - if you see Darwin in the name, it's OSX.
- linux - you guessed it.
- debian - debian and debian derivatives like Ubuntu.
- windows - no surpises here either.

**Processor architectures**

- **amd64 / x86_64 / x64** - 64-bit version. Linux users will know it as amd64. It references the 64-bit extension of the x86 instruction set (first popularized by AMD). AMD64, Intel 64, or VIA Nano chips can run this software. Choose this version if you have a 64-bit computer. This is most users.
- **386 / i386 / x86_32** - 32-bit version. Chose this version if you have a 32-bit computer. This was common on computers more than a decade ago.
- **arm** - references the ARM architecture. Used in lightwieght applications like smartphones, micro computers, and embedded systems. Think Raspberry Pi.
- **arm64** - the 64-bit flavor.

32 vs 64-bit computers

The takeaway: 32-bit computers are only capabile of handling a limited amount of RAM (think 4GB on a Windows machine). With RAM and processing power consistently on the rise, the need or

## Full Bash reference

### `cat` command - ConcATenate

Intented to combine or concatenate multiple text files into one. Used for a variety of things, like the simple `cat filename.txt` to print out a files contents.

```bash
# print out contents of file to terminal
$ cat file

# Use the more or less command to print out one page at a time
$ cat file | more
$ cat file | less

# combine multiple files
$ cat file1 file2 > megaFile


```

### `cd` - Change Directory

Probably the most rudimentary command. Allows you to traverse the file system.

```bash
$ pwd                       # print working directory - get current location
↪ /users/benish/code

$ ls                        # list out content of current directory
↪ file.txt  lounge-frontend/  lounge-backend/

$ cd lounge-frontend/       # move into "lounge-frontend"
# pwd /users/benish/code/lounge-frontend

$ cd ..                     # move up one directory
# pwd /users/benish/code
```

### `cp` - CoPy

```bash
# syntax
cp [OPTIONS] source destination
cp [OPTIONS] source directory

```

Copy a file - copies content of `file1` to `file2`. Creates file2 if it doesn't exist, overwrites it if it does.

```
cp file1 file2
```

Copy files to a directory - overwrites contents of directory if it exits, creates one if it does not. Can supply 1..n files.

```
cp file1 file2 file3 targetDirectory
```

Copy directories - copies entire contents of source directory to target directory. Creates or overwrites contents in target. Usually needs to be run recursively with the `-r` option.

```
cp -R sourceDirectory targetDirectory
```

Other `cp` commands

```bash
$ cp -i s.txt f.txt # interactive - promt before overwriting
```

### `curl` - Client URL

Transfer an URL.

```bash
# download file
`curl -O https://site.com/dowload/linux-amd64.tar.gz`
    # -O: save file locally with same name as remote file
    # -L: follow redirects (if first response is 3xx)
```

### `dig` - Domain Information Grouper

Get information about DNS name servers. Commonly used to see what domain names resolve to.

```bash
# run dig on github.com
$ dig github.com

# results
; <<>> DiG 9.10.6 <<>> github.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 47887
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
# What was queried (the defult query is for an Internet Address [A])
;; QUESTION SECTION:
;github.com.			IN	A

# "Answer" - IP of where to find github.com
;; ANSWER SECTION:
github.com.		42	IN	A	140.82.113.3

# statistics about the query
;; Query time: 28 msec
;; SERVER: 2001:558:feed::1#53(2001:558:feed::1)
;; WHEN: Sat Nov 09 21:12:49 EST 2019
;; MSG SIZE  rcvd: 55
```

``` bash
# quick dig
$ dig github.com +short
↪ 140.82.113.3

# get trace route
$ dig github.com +trace

# bring your own nameserver
$ dig @ns1.you-specify.com github.com

# trim dig output
$ dig github.com +nostats       # no stats
$ dig github.com +nocomments    # no header
$ dig github.com +noall +answer # remove everything, show answer

# Request different types of records
$ dig github.com NS
```

Request different types of records
- A = Internet Address, default (IP address)
- TXT = Text annotations
- MX = Mail eXchange (mail servers)
- NS = Name Server


### `file` command

Indicates file type.

Usage

```bash
$ file cats.md      # basic usage
↪ ./cats.md: ASCII text, with very long lines

$ file cats.md      # get MIME type
↪ ./cats.md: text/plain; charset=utf-8

$ file some-directory/* # entire contents of "some-directory"
$ file -z flash.        # content of compressed file

file /dev/sda
file -s /dev/sda
file /dev/sda5
file -s /dev/sda5

```

### `sed` - Stream EDitor

Sed is a stream editor for filtering and replacing text. Sed probably has a shit tonne of stuff going on, used commonly for REGEX string matching and replacement.

```bash
sed -i "s,TEXT_TO_FIND,TEXT_TO_REPLACE_WITH,g"
```

### `type` command

Type give the user information about the command type.

```
type [OPTIONS] FILE_NAME...
```
