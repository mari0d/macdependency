# Download & Installation #
You can either download the binary from the download section, which I provide in form of a dmg-file. You can mount that on your filesystem. The dmg-file contains only the bundle macdependency which you can copy to your applications folder /Applications or anywhere else.

If you like, you can also compile the file directly from the sources.

# Usage #
You can either open a bundle, library or framework via the menu or you can just drop any Mach-O file on the program icon or on the program itself. It then shows all dependencies as well as some other information like type, version and imported/exported symbols. The dependencies form a hierarchy, since the dependent files may have dependencies itself.

# Support #
If you find any bugs, please report them in the Issues section.

# Uninstallation #
Since macdependency writes no data anywhere, you can remove it completely by just deleting the macdependency bundle from your disk.