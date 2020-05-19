This is a summary of commonly used commands.\[1\]\[2\] We reproduce the
content of the FOSSwire cheat sheet \[3\] here. You can ![download a
PDF](FOSSwire_unix_ref.pdf "download a PDF").

A more indepth, Linux guide is available at
[Information:Linux](Information:Linux "wikilink").

## Unix/Linux Command Reference

### File Commands

  - **`ls`** - directory listing
  - **`ls`` ``-al`** - formatted listing with hidden files
  - **`cd`` `<i>`dir`</i>** - change directory to *dir*
  - **`pwd`** - show current directory (Print Working Directory)
  - **`mkdir`` `<i>`dir`</i>** - create a directory *dir*
  - **`rm`` `<i>`file`</i>** - delete *file*
  - **`rm`` ``-r`` `<i>`dir`</i>** - delete directory *dir* and all its
    contents
  - **`rm`` ``-f`` `<i>`file`</i>** - force delete file
  - **`rm`` ``-rf`` `<i>`dir`</i>** - force delete directory *dir* and
    all its contents (use with caution)
  - **`cp`` `<i>`file1`</i>` `<i>`file2`</i>** - copy *file1* to *file2*
    (overwrites *file2* if it exists)
  - **`cp`` ``-r`` `<i>`dir1`</i>` `<i>`dir2`</i>** - copy *dir1* to
    *dir2*; create *dir2* if it doesn't exist
  - **`mv`` `<i>`file1`</i>` `<i>`file2`</i>** - rename *file1* to
    *file2* (overwrites *file2* if it exists)
  - **`mv`` `<i>`file`</i>` `<i>`dir`</i>** - move *file* to directory
    *dir*
  - **`ln`` ``-s`` `<i>`file_or_dir`</i>` `<i>`link`</i>** - create
    symbolic link *link* to *file_or_dir*
  - **`touch`` `<i>`file`</i>** - create empty *file*; if *file* exists,
    updates last-modified date
  - **`less`` `<i>`file`</i>** - view contents of *file*
  - **`head`` `<i>`file`</i>** - output first 10 lines of *file*
  - **`tail`` `<i>`file`</i>** - output last 10 lines of *file*
  - **`tail`` ``-f`` `<i>`file`</i>** - output contents of *file* as it
    grows, starting with last 10 lines

### Process Management

  - **`ps`** - display your currnet active processes
  - **`top`** - display all running processes
  - **`kill `<i>`pid`</i>** - kill process id *pid* (numerical ID)
  - **`bg`** - lists stopped or background jobs; resume a stopped job in
    the background
  - **`fg`** - brings the most recent job to the foreground
  - **`fg `<i>`n`</i>** - brings job *n* to the foreground

### File Permissions

  - **`chmod `<i>`mode file`</i>** - change permissions of *file* to
    given *mode*; mode is `[ugoa...][[+-=][perms...]...]`
      - **`u, g, o, a`** : specify the owner (user), group, other, or
        all
      - **`+, -, =`** : + adds given permissions to file, - removes
        given permissions from file, = sets given permissions on file
      - **`perms` : `r, w, x`** or any combination of the three -- r
        means read permission, w means write permission, x means execute
        (file) or cd (directory) permission

### SSH

See also: [SSH Quick Start Guide](SSH_Quick_Start_Guide "wikilink")

### Searching

Better described as finding strings in files.

  - **`grep `<i>`pattern files`</i>** - print out lines containing
    *pattern* in *files*
  - **`grep -r `<i>`pattern dir`</i>** - print out lines containing
    *pattern* in all files found recursively descending directory *dir*
  - **<i>`command`</i>` | grep `<i>`pattern`</i>** - print out lines in
    the output of *command* which contain *pattern*

### System Info

  - **`date`** - show current date and time
  - **`cal`** - show this month's calendar
  - **`cal `<i>`year`</i>** - show calendar for entire *year*
  - **`uptime`** - show how long the machine has been up
  - **`w`** - display users who are logged in
  - **`whoami`** - who you are logged in as
  - **`id`** - print all user ID information for yourself
  - **`finger `<i>`user`</i>** - display information about *user*
  - **`uname -a`** - show information about machine
  - **`cat /proc/cpuinfo`** - cpu information
  - **`cat /proc/meminfo`** - memory information
  - **`man `<i>`command`</i>** - show manual for *command*
  - **`df -h`** - show disk usage
  - **`free`** - show memory and swap usage
  - **`whereis `<i>`command`</i>** - show possible paths to *command*
  - **`which `<i>`command`</i>** - show absolute path to *command*

### Compression

  - **`tar cf `<i>`dir.tar dir`</i>** - create a tar file named
    *dir.tar* containing all files in the directory *dir*
  - **`tar xf `<i>`dir.tar`</i>** - extract all files from *dir.tar*
  - **`tar zcf `<i>`dir.tar.gz dir`</i>** - create a gzipped tar file
    named *dir.tar.gz* containing all files in *dir*
  - **`tar zxf `<i>`dir.tar.gz`</i>** - extract all files from
    *dir.tar.gz*
  - **`tar jcf `<i>`dir.tar.bz2 dir`</i>** - create a tar file named
    *dir.tar.bz2* compressed with bzip2 containing all files in *dir*
  - **`tar jxf `<i>`dir.tar.bz2`</i>** - extract all files from
    *dir.tar.bz2*
  - **`gzip `<i>`file`</i>** - compress *file* and rename it *file.gz*
  - **`gzip -d `<i>`file.gz`</i>** - uncompress *file.gz* into *file*

### Network

  - **`jwhois `<i>`domain`</i>** - print administrative and contact
    information for the owner of *domain*
  - **`dig `<i>`domain`</i>** - print DNS information for *domain*
  - **`dig -x `<i>`host`</i>** - print reverse DNS lookup of *host*
  - **`wget `<i>`url`</i>** - download the file at *url*
  - **`wget -c `<i>`url`</i>** - resume a stopped download

### Installation

Typical GNU-style source packages for software follow this recipe for
building:

`   `**`[username@headnode``
``package]>`**` ./configure --prefix=$HOME`
`   `**`[username@headnode`` ``package]>`**` make >& make.out &`
`   `**`[username@headnode``
``package]>`**` make install >& make.install.out &`

### Shortcuts

  - **Ctrl-C** - halts the current command (send signal SIGINT)
  - **Ctrl-Z** - pauses the current command
  - **`fg`** - resumes a Ctrl-Z'ed command
  - **`bg`** - resumes a Ctrl-Z'ed command into the background
    (returning terminal control)
  - **`!!`** - repeats the last command
  - cursor keys Up and Down - browse command history

## See Also

  - [*Linux Pocket Guide*](http://oreilly.com/catalog/9780596006280/),
    by Daniel J. Barrett (2004)
  - [*Using csh and tcsh*](http://oreilly.com/catalog/9781565921320/),
    by Paul DuBois (1995)
  - [*bash Quick Reference*](http://oreilly.com/catalog/9780596558772/),
    by Arnold Robbins (2006)
  - [Stanford University OpenClassroom's "Practical Unix"
    class](http://openclassroom.stanford.edu/MainFolder/CoursePage.php?course=PracticalUnix)
  - [Text Editors](Text_Editors "wikilink")

## References

<references/>

[Category:Quick Start](Category:Quick_Start "wikilink")

1.  [FOSSwire Unix/Linux Command Cheat
    Sheet](http://fosswire.com/post/2007/8/unixlinux-command-cheat-sheet/)
    by Jacob Peddicord at FOSSwire.com

2.  [25+ Useful Linux and Unix Cheat
    Sheets](http://www.techieblogger.com/2009/10/linux-unix-ubuntu-solaris-cheat-sheets.html)
    by Mohamed Rias at Techieblogger.com

3.---
title: Quick Start Guide:Linux Commands
permalink: /Quick_Start_Guide:Linux_Commands/
---

