# Week 04 - Boost Notes

## Why have $HOME if I am the only person working on this computer
- Traditionally Unix computers were used by multiple Users w/ different Permissions
- Preventing Priveledge Escalations, since the permissions of the User is less than the permissions of the system.
- Primary reason to have your user directory when each computer is used by one user is `CONTAINERS`

## What are permissions and why do I care?
First thing a hacker gets into your system they will run a permission check and will try to find some gaps on these set of permissions.

- `ls -l .` Get the permission sets on the 'current directory'.
- `ls -d ` Lists directories not contents of the directories
- `ls -li` Gives the inode information for listed files
> There is a certain limit if the size of the file is below that content is saved to inode table meaning opening directory means opening the file content. This very interesting I should go down this rabbit-hole sometime

File and Directory permissions are set in 3 sets of 3 bits, File permissions are different from Directory permissions.
 - `ls . -l` ( Might return permission denied )
 - `ls foo.md -l` ( Permission given on file )
 - `chmod {u,o,g,a}{+,-,=}{r,w,x} {file-name}` - adds or removes permissions.


## Guts of an `inode`
> If you want to be the jack the ripper of the inodes you should be use `stat`

- `stat <file-name>` will display all the details on `<file-name>` inode.
- Remember everything is an inode ("file")

## References:
- https://www.picoctf.org/ 