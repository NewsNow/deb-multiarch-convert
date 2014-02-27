deb-multiarch-convert
=====================

Converts Debian binary package files to multiarch.

deb-multiarch-convert provides a convenient way to create
Debian multiarch-compatible binary package files in certain restricted circumstances,
where modifying the source package to make the build multiarch-compatible would be too onerous.

Usage: deb-multiarch-convert <file>

<file> must be a valid Debian binary package and must be either:

  a. an i386- or amd64-specific library package, containing only architecture-specific library files
     in /lib or /usr/lib and architecture-independent files in /usr/share and possibly /etc;
     such package files will be modified to install library files into the correct new filepath,
     and marked 'Multi-Arch: same'

  b. an architecture-independent package (Architecture: all);
     such package files will be marked 'Multi-Arch: foreign'

In all cases, a modified package will have '+multiarch' appended to the existing version string.

WARNING: This script does not yet check that your chosen package does
only contain the types of files suitable for this conversion - that
remains up to you! No liability by the authors is accepted for any use
or misuse of this software.
