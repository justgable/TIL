# Remove old system kernels

When trying to `sudo apt-get upgrade` on my Ubuntu 16.04 server I ran into the
following error:

```
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-101-generic : Depends: linux-image-4.4.0-101-generic but it is not installed
 linux-signed-image-4.4.0-101-generic : Depends: linux-image-4.4.0-101-generic (= 4.4.0-101.124) but it is not installed
E: Unmet dependencies. Try using -f.
```

Running the recommended `sudo apt-get -f install` failed due to a lack of space
on /boot. Checking the file system with `df -h` showed that it was indeed full.

DuckDuckGo'ing led me to [this knowledge base article](https://help.ubuntu.com/community/RemoveOldKernels#Safely_Removing_Old_Kernels)

## Why it's necessary

> For users of LVM systems, encrypted systems or limited-storage systems, the most frequent problem is that the /boot partition is simply full. The package manager cannot install a pending upgrade due to lack of space. Addiitionally, apt-get can not remove a package due to broken dependency.

> This problem can be fixed from the shell: by manually remvoing one or two old kernels, we can provide the package manager enough space to install the queued upgrade.
