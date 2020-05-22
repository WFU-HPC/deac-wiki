# What is SSH?

**SSH** provides an encrypted terminal session from one computer to
another: all commands that you type and all output from the remote
machine are scrambled. It normally communicates over port 22.

# Getting Started

## Linux/Unix/Mac OS X

  - Start a terminal program
  - Type the command -- note that that is an uppercase "X", not
    lowercase:

`   `**`[username@mycomp`` ``~]>`**` ssh -A -Y username@<headnode.deac>`

  - If this is your first time connecting, you will get a
warning:

`   The authenticity of host 'headnode.deac (152.17.36.129)' can't be established. `
`   RSA key fingerprint is  13:75:40:c7:fe:dd:f2:83:63:9a:6a:f6:53:77:5b:52 `
`   Are you sure you want to continue connecting (yes/no)? yes `
`   Warning: Permanently added '<headnode.deac>' (RSA) to the list of known hosts.`

  - At the "Are you sure you want to continue connecting?" prompt, you
    must type in the full word "yes".
  - The "-X" (uppercase X) option allows "X11 forwarding" so that
    GUI-based applications can be displayed on the local machine

## Windows

You will need the PuTTY\[1\] program. Using PuTTY is more complicated
than using ssh in Linux. You will need to set up "profiles" for each
host you wish to connect to.

  - PuTTY is installed on your WFU laptop as part of the standard load.
  - Otherwise, you may [download
    it](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html).
    (Choose putty.exe.)
  - The first time you run PuTTY, you will see:
    ![Putty_01.png](Putty_01.png "Putty_01.png")
  - To create a new profile:
      - enter a hostname or IP address in the "Host Name (or IP
        Address)" box near the top of the window; make sure the "SSH"
        button is selected
      - enter the same host name in the empty box right below "Saved
        Sessions"
      - in the left sidebar (Category:), click on "Data" in the
        "Connection" category -- you will see a new form on the right
      - in the "Login Details" section, enter your own username in
        "Auto-login username ![Putty_02_1.png](Putty_02_1.png
        "Putty_02_1.png")
      - then, click back on the "Session" category in the left sidebar,
        and click the "Save" button
  - To connect to the host, double-click the saved session name.
  - If it is the first time you are logging into a headnode from this
    Windows machine, you will see a "security alert" -- just click "Yes"
    to continue connecting: ![Putty_04.png](Putty_04.png
    "Putty_04.png")

For more information, including getting GUI applications from the
cluster to display on your Windows computer, see [Using the Cluster from
a Windows system](Using_the_Cluster_from_a_Windows_system "wikilink").

# See Also

## Training Video

  - [DEAC Login with PuTTY Training
    Video](https://youtu.be/3rl7otU9Evw?list=PL-g8n27Db1XfPrRvZMBSxK55_lIy39sqZ)

## Helpful Links

  - [SSH Tutorial for
    Linux](http://support.suso.com/supki/SSH_Tutorial_for_Linux)
  - [Public key-based
    authentication](http://sial.org/howto/openssh/publickey-auth/)
    (passwordless logins)

# References

<references/>

[Category:Quick Start](Category:Quick_Start "wikilink")

1.  [PuTTY: A Free Telnet/SSH
    Client](http://www.chiark.greenend.org.uk/~sgtatham/putty/), by
    Simon Tatham
