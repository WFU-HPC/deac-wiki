## Required Software

An SSH client. SSH (Secure SHell) gives you an encrypted terminal
session to the head nodes.
[PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/) should be
installed on your WFU issued laptop. If it is not, you may download it
from [PuTTY's download
site](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html).

  - **NOTE:** Be sure to download the "Windows installer" binary so that
    it will do all the dirty work for you.

## Recommended Software for Remote Display

An X11 Server. Opening graphical windows from the cluster requires
Windows to support the X11 protocol. An open source X11 client,
[Xming](http://www.straightrunning.com/XmingNotes/), is available for
download.

## Windows Configuration Steps

  - In PuTTY, the "X11 Forwarding" setting must be checked on (see image
    below) -- it's under Connection -\> SSH -\> X11:

![Putty_x11_forwarding.png](Putty_x11_forwarding.png
"Putty_x11_forwarding.png")

  - For basic X11 forwarding, use
    [Xming](http://www.straightrunning.com/XmingNotes/)\[1\]
  - For advanced X11 forwarding, use
    [Cygwin/X](https://x.cygwin.com/docs/ug/cygwin-x-ug.html)\[2\][Cygwin/X](https://x.cygwin.com/docs/ug/cygwin-x-ug.html)</ref>

![Windows_start_xming.png](Windows_start_xming.png
"Windows_start_xming.png")

### More Conveniences

  - [PuTTY Session Manager](http://puttysm.sourceforge.net/) - displays
    a list of all saved sessions in order to quickly launch them

![Desktop_putty_sm.png](Desktop_putty_sm.png "Desktop_putty_sm.png")

## See Also

  - [Quick Start Guide:SSH](Quick_Start_Guide:SSH "wikilink") -- more
    details on using PuTTY on Windows, including some information on the
    PuTTY Sessions Manager which keeps a list of saved sessions always
    available

## References

<references/>

[Category:New User
Information](Category:New_User_Information "wikilink")
[Category:Cluster](Category:Cluster "wikilink")

1.  [Xming](http://www.straightrunning.com/XmingNotes/)

2.---
title: Cluster:Using from Windows
permalink: /Cluster:Using_from_Windows/
---

