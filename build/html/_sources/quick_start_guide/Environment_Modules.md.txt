The modules\[1\] package allows you to modify your environment to use
specific versions of software you may need. More importantly, it allows
you to easily undo those modifications if you need to use a different
package or version.

## Introduction and Basic Use

Let's say you need to do compilations with Intel Cluster Studio 2012
with 4-byte integers. You would set up your environment (paths, library
paths, etc) by doing:

`   $ module load compilers/intel-2012-lp64`

You would use this in [SLURM](Software:SLURM "wikilink") scripts, too,
because the resulting executable may need to know the paths to the
dynamic libraries to which it is linked. If you no longer need to use
that particular compiler, you would do:

`   $ module unload compilers/intel-2012-lp64`

To switch to a different compiler, you would unload and then load the
environment for the new compiler:

`   $ module unload compilers/intel-2012-lp64`
`   $ module load compilers/pgi-XXX`

You can see modules you have
loaded:

`   $ module list`
`   `
`   Currently Loaded Modulefiles:`
`     1) dot                         2) use.own                     3) compilers/intel-2012-ilp64`

You can see all available modules that may be
loaded:

`   $ module avail`
`   `
`   -------------------------------------- /usr/share/Modules/modulefiles ---------------------------------------`
`   dot           module-cvs    module-info   modules       mpich2-x86_64 null          use.own`
`   `
`   --------------------------------------------- /etc/modulefiles ----------------------------------------------`
`   mvapich-psm-x86_64 mvapich-x86_64     mvapich2-x86_64`
`   `
`   ---------------------------------------- /home/username/privatemodules ----------------------------------------`
`   compilers/foobar-0.1       compilers/intel-2012-ilp64 compilers/intel-2012-lp64  null`

You can get brief information about a
module:

`   $  module whatis compilers/intel-2012-ilp64`
`   compilers/intel-2012-ilp64: Sets up to use the Intel Cluster Studio 2012 compilation environment with 8-byte integers.`

And longer
information:

`   $ module help compilers/intel-2012-ilp64`
`   `
`   ----------- Module Specific Help for 'compilers/intel-2012-ilp64' ---------------------------`
`   `
`           Sets up to use Intel Cluster Studio XE/Composer XE compilers and tools - 8-byte integers`
`           Includes: C/C++ 12.1.0, Fortran 12.1.0, Debugger 12.1,`
`           Inspector XE 12.0, Trace Analyzer, VTune Amplifier,`
`           Intel MPI/OpenMP 4.0.3, MPI Benchmarks 3.2.3,`
`           Intel Performance Primitives, Thread Building Blocks,`
`           Math Kernel Library, Cilk`
`   `
`           Version 2012`

## Use in Shell Scripts and [SLURM](Software:SLURM "wikilink") Job Scripts

Incorporating the module command into shell scripts will depend on the
shell that you use: bash or tcsh.

### bash/sh/ksh

Bash scripts, by default, do not execute system-wide login scripts (i.e.
the scripts in /etc/profile.d). Since the "module" command is provided
by one of the login scripts in /etc/profile.d, that means doing "module
load somemodule" in your script will fail, in general. There are two
ways to fix this:

1.  Run bash as a login shell: in the first line of your script, do
    "**`#!/bin/bash`` ``-l`**"
2.  Manually execute the modules login script: in the early part of your
    script, do "**`.`` ``/etc/profile.d/modules.sh`**"

### tcsh/csh

Tcsh scripts, by default, *do* execute system-wide login scripts, so the
"module" command should be available.

However, if you generally use "**`#!/bin/tcsh`` ``-f`**", you will have
to add "**`source`` ``/etc/profile.d/modules.csh`**" to the early part
of your script. This is because the "-f" option to tcsh says not to
source any login scripts or perform command hashing for faster startup.
This speed difference is not really noticeable on modern systems.

## Modulefiles

Systemwide modulefiles are located in: /usr/share/Modules/modulefiles
and /etc/modulefiles. Each user may write their own module files, and
put them in ~/privatemodules. There may be subdirectories in the module
directories. Subdirectory names will be part of the module name, e.g.
the module file ~/privatemodules/compilers/intel-2012-ilp64 provides the
module named "compilers/intel-2012-ilp64".

More information is available in the man page for modulefile.\[2\]

Before you will be able to use your own module files, you must load a
module that allows you to use your own modules:

`   $ module load use.own`

### Things to Note

Modulefiles are in an extended version of the Tcl scripting language.
One important thing to note is that environment variables that are used
in one part of the script may not be used in another because the
environment variable is not yet set in the environment:

`   # `**`THIS`` ``WILL`` ``NOT`` ``WORK`**
`   setenv FOOBAR "/foobar"`
`   setenv FOOBAR_BIN "$FOOBAR/bin"`

You will need to use variables defined in the Tcl script:

`   # Set a variable in Tcl`
`   set foobar "/foobar"`
`   setenv FOOBAR "$foobar"`
`   setenv FOOBAR_BIN "$foobar/bin"`

Other things to note:

  - TCL considers "_" (underscore) as part of a variable name, but not
    "-" (hyphen).
      - So, `$foo_bar`, `${foo_bar}` are equivalent: they are the same
        variable **foo_bar**
      - And, `$foo-bar` and `${foo}-bar` are equivalent: that is the
        variable **foo** appended by the string "-bar"
  - If you want to use "_" as a separator, you will have to either
    group the variable name in a pair of braces {}, or escape the
    underscore with a backslash:
      - `${foo}_bar` -- this is **foo** appended with "_bar"
      - `$foo_bar` -- this is also **foo** appended with "_bar"

## Known Bugs

Sometimes, the module command will crash when doing a "module unload".
It will print out a long error message. If this happens, do "cd" to go
back to your home directory, and repeat the "module unload" command. If
that still does not work, you will have to log out and back in.

## Troubleshooting

### Command Not Found

; Login Shell : /bin/bash

; Error Message in Job Script : **module: command not found**

</pre>

  - Note: all other subsequent error messages in your job output can
    most likely be ignored in troubleshooting this problem as they are
    most likely a result of the missing environment setup the module
    command would have provided.

#### Solution

  - As a BASH shell user, the 'module' system does not load modules
    automatically. To allow for environment modules to be used in your
    batch script, add the following line to your (after the \#SBATCH
    directives):

<!-- end list -->

  -

        . /etc/profile.d/modules.sh

## Example

Here is an example modulefile for Mathematica
    8.0.4:

    #%Module########################################################################
    ##
    ## mathematica-8.0.4 modulefile
    ##

    # for Tcl script use only
    set     version        8.0.4
    set     mathematicadir /deac/opt/mathematica-$version/bin

    proc ModulesHelp { } {
        global version

        puts stderr "    This module sets up the environment to use Mathematica $version"
        puts stderr "    To run remotely, you may need to install the Mathematica fonts:"
        puts stderr "    http://support.wolfram.com/technotes/latestfonts.en.html"
    }

    module-whatis   "Sets up the environment to use Mathematica $version"

    prepend-path PATH $mathematicadir

## References

<references/>

[Category:Quick Start](Category:Quick_Start "wikilink")

1.  [Modules -- Software Environment Management: project page at
    Sourceforge](http://modules.sourceforge.net/)
2.  [modulefile man
    page](http://modules.sourceforge.net/man/modulefile.html)
