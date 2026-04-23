# Permission Management
**Permission management** controls who can **read, write, or execute** files and directories.

1. r ----------> read (4)  
2. w -----------> write (2)      
3. x -----------> execute (1) 
4. (-) -----------> no permission (0)
 - total sum is 7

1. chmod ---------- to change permission
2. chown ----------- to change owner
3. chgrp ------------ to change group


u ----------> user / owner	

g ----------> group	

o ---------> other		               	

 - 	Add (+)
 - 	remove (-)
 - 	set (=)

Ex. 1. chmod ugo+rwx 

Ex. 2. chmod 777

1.  `-r-xr-xr-x 1 root root 0 Jul 29 20:06 student` 
 - filename permissions
 - links
 - username
 - group name
 - file size
 - date & time
 - filename
2. `-rw-rw-r-- 1 root root 0 Apr 25 21:20 (file2)`
   - file type
   - permission modes
   - link count
   - ownership
   - file size
   - time stamp
   - file names
----

## file type
1. user defined files
 - d  ------  dir.
 - (-)  ------  normal file
 - l  ------  linked file
2. system defined files
 - b  -------  block device file
 - c  -------  character device file
 - p  -------  pipe file
 - s  -------  socket device file


dir. linked count = 2 
file linkedd count = 1
