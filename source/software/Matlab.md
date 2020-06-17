## Preliminaries

To run MATLAB, you must load a MATLAB module to set up your environment.
See [Quick Start Guide:Matlab](Quick_Start_Guide:Matlab "wikilink").

You can have your own library of Matlab functions and routines. The
default location is: `~/matlab/`. Matlab will also look in the current
directory. This is akin to the `PATH` environment variable in your
shell.

## Matlab from the command line

It is possible to run Matlab without the graphical user interface:

`   [username@headnode]> use-student-matlab -nodesktop -nosplash`

## Non-interactive Matlab

Let's say you have the following script, named `randarr.m` in
`~/matlab`:

`   A = rand(5, 5)`
`   quit`

You can run the script non-interactively by doing the following in the
shell:

`   [username@headnode]> use-student-matlab -r randarr -nodesktop -nosplash`
`   `
`   Using Matlab directory /deac/opt/matlab-2012a/bin to find executable...`
`   `
`                                     < M A T L A B (R) >`
`                           Copyright 1984-2012 The MathWorks, Inc.`
`                            R2012a (7.14.0.739) 64-bit (glnxa64)`
`                                      February 9, 2012`
`   `
`       `
`    `
`   To get started, type one of these: helpwin, helpdesk, or demo.`
`   For product information, visit www.mathworks.com.`
`   `
`   A =`
`   `
`   0.8147    0.0975    0.1576    0.1419    0.6557`
`   0.9058    0.2785    0.9706    0.4218    0.0357`
`   0.1270    0.5469    0.9572    0.9157    0.8491`
`   0.9134    0.9575    0.4854    0.7922    0.9340`
`   0.6324    0.9649    0.8003    0.9595    0.6787`

You can create a shell script to run the program, too. Name it, say,
`randarr.sh`:

`#!/bin/bash`
`. /etc/profile.d/modules.sh`
`module load matlab-2017a`
`/usr/local/bin/use-student-matlab -r randarr -nodesktop -nosplash`

You are not limited to placing Matlab scripts in `~/matlab/`. You can
place them anywhere, and have Matlab run them. E.g.

`#!/bin/bash`
`# This assumes the script ~/Analysis/crunch_numbers.m exists`
`. /etc/profile.d/modules.sh`
`module load matlab-2017a`
`   `
`ANALYSISDIR=~/Analysis`
`CRUNCH=crunch_numbers`
`MATLAB=/usr/local/bin/use-student-matlab`
`cd $ANALYSISDIR && $MATLAB -r $CRUNCH -nodesktop -nosplash`

## Submitting a Matlab computation to the cluster

Creating a Matlab job for the cluster is a short step away. Create a job
script that calls Matlab as
above:

`#!/bin/bash`
`#SBATCH --partition=small`
`#SBATCH --mail-user=username@wfu.edu`
`#SBATCH --mail-type=BEGIN,END,FAIL`
`#SBATCH --output=matlab_job-%j.o`
`#SBATCH --error=matlab_job-%j.e`
`#SBATCH --account=generalGrp`
`#SBATCH --nodes=1`
`#SBATCH --tasks-per-node=1`
`#SBATCH --mem=8gb`
`#SBATCH --time=05:00:00`
`   `
`# set up to use modules -- N.B. this is bash-specific`
`. /etc/profile.d/modules.sh`
`module load rhel7/matlab-2017a`

`# Say that the Matlab script you want to run is: ~/Analysis/crunch_numbers.m`
`   `
`cd /deac/workingGrp/username/Analysis`

`MFILE=crunch_numbers.m`
`MATLAB=/usr/local/bin/use-student-matlab`
`OPTIONS="-nodesktop -nosplash"`
`OUTPUT=crunch_numbers.${SLURM_JOB_ID}.result`

`$MATLAB -r "run('$MFILE');" $OPTIONS &> $OUTPUT`

  - NOTE: Instead of using the -r "run()" method, Matlab can also be
    executed via I/O redirection as well:

`cd $WORKDIR && $MATLAB $OPTIONS <$MFILE  &> $OUTPUT`

Please see [the article on using
modules](Quick_Start_Guide:Environment_Modules "wikilink") for csh/tcsh
commands.

## See Also

  - [Quick Start Guide:Matlab](Quick_Start_Guide:Matlab "wikilink")

## References

<references/>

[Category:Software](Category:Software "wikilink")[Category:Quick Start](Category:Quick_Start "wikilink")
