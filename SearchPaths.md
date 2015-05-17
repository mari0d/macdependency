# Introduction #
Not all dependencies are given with an absolute file name, so the dynamic loader dyld (sometimes also called dynamic link editor) has to figure out where to find those files. There is a search order of predefined paths to which the dyld sticks to. Unfortunately the documentation from apple regarding this point is very weak and often contradictory. Therefore I used the source file of the latest dyld (http://www.opensource.apple.com/source/dyld/dyld-97.1/src/dyld.cpp) to find out how the dyld really works.

# Details #

First of all the dependent filename is stripped, so that only the filename without any path information is extracted. Then the dyld tries to find the file in different directories in the following order. As soon as the file is found, the mechanism terminates:

  1. find filename in all paths given by LD\_LIBRARY\_PATH (separated by ":")
  1. if filename is a framework: find framework name (without path information) in all paths given by DYLD\_FRAMEWORK\_PATH (separated by ":")
  1. find filename in all paths given by DYLD\_LIBRARY\_PATH (separated by ":")
  1. if filename starts with @executable\_path, @loader\_path or @rpath those strings are replaced by the path of the current executable, the path of the binary which depends on this file or the given RPATHs (see http://www.mikeash.com/pyblog/friday-qa-2009-11-06-linking-and-install-names.html)
  1. find filename (including original path information)
  1. if filename is a framework: find framework name (without path information) in all paths given by DYLD\_FALLBACK\_FRAMEWORK\_PATH (separated by ":"). If this environment variable isn't set, it instead looks in the following default paths: ~/Library/Frameworks,/Library/Frameworks,/Network/Library/Frameworks,/System/Library/Frameworks
  1. find filename in all paths given by DYLD\_FALLBACK\_LIBRARY\_PATH (separated by ":"). If this environment variable isn't set, it instead looks in the following default paths: ~/lib,/usr/local/lib,/lib,/usr/lib
