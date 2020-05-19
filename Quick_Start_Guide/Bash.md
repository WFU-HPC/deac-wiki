**bash** is the Bourne Again Shell\[1\] (based on **sh**, the Bourne
shell). It is part of the [GNU Project](http://www.gnu.org/home.html).

## Syntax

Here is a brief outline of common syntax issues.

### Login/Logout Scripts

The startup files used depend on whether the session is interactive or
not, and whether it is a login shell.\[2\]

  - ~/.bash_profile
  - ~/.bash_login
  - ~/.profile
  - ~/.bashrc
  - ~/.bash_logout

### Aliases

The syntax for defining aliases is:

`   alias ls='ls -FC --color=auto'`
`   alias l='ls'`
`   alias ll='l -l'`
`   alias la='ll -a'`

### Environment Variables

The syntax for defining environment variables is:

`   export SPECIAL_ENV=some_string_or_other`
`   export VERY_SPECIAL_ENV=${SPECIAL_ENV}:another_string`

## See Also

  - The [GNU info standalone
    manual](http://www.gnu.org/software/texinfo/manual/info-stnd/) is a
    complete hyperlinked online manual
  - The man page is terse but useful for quick lookups
  - The [online
    manual](http://www.gnu.org/software/bash/manual/bashref.html) covers
    the latest release. It contains information identical to the info
    page.
  - [*bash Quick Reference*](http://oreilly.com/catalog/9780596558772/)
    by Arnold Robbins (2006)
  - [*Learning the bash
    Shell, 3/e*](http://oreilly.com/catalog/9780596009656/) by Cameron
    Newham (2005)

## References

<references/>

[Category:Quick Start](Category:Quick_Start "wikilink")
[Category:Software](Category:Software "wikilink")
[Category:Languages](Category:Languages "wikilink")

1.  [bash official website](http://www.gnu.org/software/bash/)
2.  [bash Startup
    Files](http://www.gnu.org/software/bash/manual/bashref.html#Bash-Startup-Files)---
title: Quick Start Guide:Bash
permalink: /Quick_Start_Guide:Bash/
---

