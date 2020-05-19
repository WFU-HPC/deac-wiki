## Versions

As of 14 July 2017, installed versions of MATLAB includes:

  - **MATLAB 2017a**
  - **MATLAB 2016a**
  - **MATLAB 2015a/b**
  - **MATLAB 2014a**
  - **MATLAB 2012a**
  - **MATLAB 2011a/b**

To use Matlab, load the appropriate
[module](Quick_Start_Guide:Environment_Modules "wikilink") with
corresponding version:

`    $ module load matlab-2017a`

## Licensing

The licensing package currently provided by Wake Forest University
allows for a large number of class room uses (termed **student**
licenses) and a very limited number of research licenses (termed
**faculty** licenses). Please do not be deceived, students doing
research for a faculty member or for a thesis should use the **faculty**
license.

### Student / Research Licenses

To load the appropriate license, after loading the appropriate
environment module, use one of these scripts below based on your
institution.

For students doing coursework at the Reynolda campus:

`    $ use-student-matlab`

For students or faculty/staff doing research at the Reynolda campus:

`    $ use-faculty-matlab`

These scripts behave like the plain **matlab** command - they merely set
the appropriate license before running MATLAB itself. Please note that
the description of the two licenses provided here is not detailed or
comprehensive of the restrictions. Users who are concerned about whether
their usage falls into the student or faculty class should contact the
HPC Team (deac-help@wfu.edu) and request assistance in determining the
proper license to use.

### Available Licenses

The following is a list of the available licenses for research use (not
classroom/educational use) for Matlab. This license information is
specific to the Reynolda Campus\! WFUHS Matlab license information is
different and available only the WFUHS users.

The list below was created on 10:00, 14 July 2017 (UTC):

:;MATLAB : 30

:;Bioinformatics_Toolbox : 2

:;Curve_Fitting_Toolbox : 7

:;Data_Acquisition_Toolbox : 1

:;GADS_Toolbox : 1

:;Image_Acquisition_Toolbox : 6

:;Image_Toolbox : 15

:;MATLAB_Builder_for_Java : 2

:;Compiler : 2

:;MAP_Toolbox : 5

:;Neural_Network_Toolbox : 2

:;Optimization_Toolbox : 12

:;Distrib_Computing_Toolbox : 12

:;PDE_Toolbox : 2

:;Signal_Toolbox : 5

:;Statistics_Toolbox : 14

:;Symbolic_Toolbox : 5

:;Wavelet_Toolbox : 2

What that means:

:\* Everyone using Matlab must check out a **MATLAB** license, resulting
in a maximum of 30 Matlab processes that can be concurrently started for
research use.

:\* Toolboxes in MATLAB provide extra functionality. That functionality
requires a supplemental license checkout. The maximum number of
concurrent licenses for each toolbox are listed above.

::\* For example, even though 30 Matlab sessions can be started, only 6
of those 30 can use the Image_Acquisition_Toolbox (for example).

:\* Each license check out is ***PER SESSION***. So, one **person** on
the cluster submitting 30 MATLAB jobs could starve the rest of campus
from using Matlab for the duration of the job.

## Documentation

MathWorks maintains reference material for the versions of Matlab that
we have installed. However, since they are not the most current ones,
the reference material is in Mathworks's archive. To access them, you
will need to register for an account at MathWorks. Once you have
confirmed your registration, you will need to attach your account to a
license. You can do that by providing the license number for Matlab:
just issue the **ver** command in Matlab, and it will display the
license number.

  - [R2017a Release
    Notes](https://www.mathworks.com/help/relnotes/?s_tid=rel_note)
  - [R2012b (7.14.0.739) MathWorks
    Documentation](http://www.mathworks.com/help/)

## See Also

  - Once loaded, learn to submit jobs by reading
    [Software:Matlab](Software:Matlab "wikilink")

## External Links

  - [MathWorks - MATLAB product
    page](http://www.mathworks.com/products/matlab/)

[Category:Software](Category:Software "wikilink") [Category:Quick
Start](Category:Quick_Start "wikilink")
[Category:License](Category:License "wikilink")---
title: Quick Start Guide:Matlab
permalink: /Quick_Start_Guide:Matlab/
---

