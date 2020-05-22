## About

HDF5 is a data model, library, and file format for storing and managing
data. It supports an unlimited variety of datatypes, and is designed for
flexible and efficient I/O and for high volume and complex data. HDF5 is
portable and is extensible, allowing applications to evolve in their use
of HDF5. The HDF5 Technology suite includes tools and applications for
managing, manipulating, viewing, and analyzing data in the HDF5 format.
\[1\]

## Version

Version installed on the cluster:

:\*
1.8.11

## Compiling

  - Configure:

`    module load openmpi/1.6-intel`
`    module load szip/2.1-intel-2012`
`    ./configure --prefix=/deac/opt/hdf5-1.8.11/intel-2012/ --with-szlib=$SZIP_DIR --enable-gpfs --enable-fortran --enable-cxx`

## References

<references/>

[Category:Software](Category:Software "wikilink")
[Category:Compiling](Category:Compiling "wikilink")

1.  [HDF5 Web site](https://support.hdfgroup.org/HDF5/)
