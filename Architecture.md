# Overview #
MacDependency consists out of two separate projects
  * MacDependency, which contains the Cocoa GUI as well as some checking functionality for existing dependencies.
  * MachO, which provides access to the properties of Mach-O files in the form of a static library (mostly platform independent code).

# Used Libraries #
MachO uses some libraries from boost
  * [filesystem](http://www.boost.org/doc/libs/1_40_0/libs/filesystem/index.html) for file handling
  * [system](http://www.boost.org/doc/libs/1_40_0/libs/system/doc/index.html) as dependent library from filesystem
  * [process](http://www.highscore.de/boost/process/) (still in incubation) to start c++filt for demangling file names