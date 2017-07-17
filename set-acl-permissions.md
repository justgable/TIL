# Use ACL on Ubuntu

## Install ACL on Ubuntu

`sudo apt-get install acl`

Filesystem is already configured for ACL for Ubuntu 14.04 >=

[Ubuntu wiki documentation](https://help.ubuntu.com/community/FilePermissionsACLs)

## List ACL for file or directory

`getfacl /my/dir`

## Set ACL for file or directory

`setfacl g:group_name:rwx /my/dir`

Use `-R` for recursive setting

## Set default ACL for directory

`getfacl -a /my/dir | setfacl -d -M- /my/dir`

This will ensure all new files and directories created under the parent directory will have the default ACL rules applied.
