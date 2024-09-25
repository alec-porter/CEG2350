## Lab 07

- Name:  Alec Porter
- Email:  porter.223@wright.edu

## Part 1

1. Command: lsblk /dev/xvda
```
NAME     MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
xvda     202:0    0   16G  0 disk 
├─xvda1  202:1    0 15.9G  0 part /
├─xvda14 202:14   0    4M  0 part 
└─xvda15 202:15   0  106M  0 part /boot/efi
```

2. Command: sudo parted /dev/xvda print
```
Model: Xen Virtual Block Device (xvd)
Disk /dev/xvda: 17.2GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
14      1049kB  5243kB  4194kB                     bios_grub
15      5243kB  116MB   111MB   fat32              boot, esp
 1      116MB   17.2GB  17.1GB  ext4
```

3. For the `xvda` partition table:
    - Does it use MBR or GPT?  GPT
    - How many partitions are on the block device? 3
    - What is the largest partition? Partition #1 at 17.2GB

4. Command: blkid /dev/xvda\*
```
/dev/xvda1: LABEL="cloudimg-rootfs" UUID="b78b2f9f-3a08-427a-ad4e-4a04f235761c" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="5685b7d3-4911-4237-9405-e73d2d78ca3e"
/dev/xvda15: LABEL_FATBOOT="UEFI" LABEL="UEFI" UUID="4B1C-F903" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="1dcb7fe9-f679-4d8b-afbe-2f4f444c7095"
```

5. For the primary partition:
    - What partition is the root filesystem on? /dev/xvda1
    - What is the partition label?  clouding-rootfs
    - What type of filesystem is on the partition?  ext4

6. Command:  df -h
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        16G  2.3G   14G  15% /
tmpfs           484M     0  484M   0% /dev/shm
tmpfs           194M  848K  193M   1% /run
tmpfs           5.0M     0  5.0M   0% /run/lock
/dev/xvda15     105M  5.3M  100M   5% /boot/efi
tmpfs            97M  4.0K   97M   1% /run/user/1000
```

7. For the root filesystem:
    - What is the total size? 16G
    - How much space is used? 2.3G
    - Where is it mounted to? /
 
8. Command: cat /etc/fstab
```
LABEL=cloudimg-rootfs	/	 ext4	discard,errors=remount-ro	0 1
LABEL=UEFI	/boot/efi	vfat	umask=0077	0 1
```

9. Fields & purpose of fields in entry that mount the root filesystem
```
Field 1 (fs_spec) - describes block special device, gives the label instead of device name:
LABEL=clouding-rootfs
Field 2 (fs_file) - describes the mount point:
/
Field 3 (fs_vfstype) - describes the type of filesystem:
ext4
Field 4 (fs_mntops) - decribes mount options in comma-seperated list:
discard - contols the use of TRIM for SSDs
errors=remouint-ro - specify behavior on critical errors which will be remount in read-only mode
Field 5 (fs_freq) - determine which filesystems need to be dumped:
0 (don't dump)
Field 6 (fs_passno) - determine order in which filesystem checks are done at boot:
1 (root filessystem should use 1)
```

## Part 2

1. `gdisk` main menu options
   - `p`:  display basic partition summary data
   - `o`:  clear out all partition data
   - `n`:  create new partition
   - `i`:  show detailed partition information
   - `w`:  write data

2. Partition table on `/dev/xvdb`
```
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINTS
xvdb    202:16   0   4G  0 disk 
└─xvdb1 202:17   0   4G  0 part
```

3. Steps to create a partition table and partition on `xvbd`
```
sudo gdisk /dev/xvdb
o
n (hit enter to accept all defaults)
w (enter Y to proceed)
```

4. Answer these questions:
   
   a. What device name does the partition use?
      - Answer: xvdb1 
        
   b. What size is the partition in GB?
      - Answer: 4G
        
   c. What filesystem type will be used on the partition?
      - Answer: Linux filesystem

## Part 3

1. Commands used: sudo mkfs -t ext4 /dev/xvdb1
2. Commands used: blkid /dev/xvdb\*
```
/dev/xvdb1: UUID="09f90404-e34e-4458-a5ca-46501f777261" BLOCK_SIZE="4096" TYPE="ext4" PARTLABEL="Linux filesystem" PARTUUID="87b4dfd0-987a-4c0c-9108-4721a1d2bd4c"
```
3. Commands used: sudo mkdir /mnt/newworld
4. Commands used: sudo mount /dev/xvdb1 /mnt/newworld
5. Contents of `/mnt/newworld`:
```
sudo chown ubuntu:ubuntu /mnt/newworld
touch file.txt
touch temp.txt
mkdir folder
mkdir data
ls -lh
total 32K
drwxrwxr-x 2 ubuntu ubuntu 4.0K Mar 13 00:26 data
-rw-rw-r-- 1 ubuntu ubuntu    5 Mar 13 00:26 file.txt
drwxrwxr-x 2 ubuntu ubuntu 4.0K Mar 13 00:26 folder
drwx------ 2 root   root    16K Mar 13 00:15 lost+found
-rw-rw-r-- 1 ubuntu ubuntu    5 Mar 13 00:26 temp.txt

```
6. Commands used: sudo umount /mnt/newworld
7. When can I interact with files on the filesystem on the partition in `xvdb`?
   - Answer: Only when the device is mounted
   
## Part 4

1. Commands used: sudo cp /etc/fstab /etc/fstab.bak | ls -l | grep fstab
2. Line you added to `/etc/fstab`: UUID="09f90404-e34e-4458-a5ca-46501f777261" /mnt/newworld ext4 defaults 0 0
3. How did you confirm that the mount point changed? (Commands used or explain process):
unmounted the partition,
verified partition no longer mounted,
remounted all filesystems via fstab,
verified partition mounted 
```
sudo umount /mnt/newworld
lsblk
sudo mount -a
lsblk
```
4. **If you restored `/etc/fstab`**, write here why you did not feel comfortable leaving your changes in place


## Part 5

1. Commands used:  touch fake1.txt | touch fake2.txt (then vim into the files and write randominfo)
2. What does the `strings` command do?
   - Answer: according to the manual it is mainly useful for determining the contents of non-text files.
3. Write a short explanation of what you saw in `strings` output: it basicllay outputs the contents of the partition: mount point, files, folders, etc.  It also listed 'vEH3' which I never figured out what it represented (Google failed me!)   
4. Commands used: rm fake1.txt
5. Is the secret you deleted still showing up in the `strings` output?  Yes, but randomly so I have to let it run for a little while.

### Report: How to Permanently Delete a File

shred -zvu -n 5 fake2.txt
-z Overwrites with zeros
-v Dispalys progress
-u Removes file after overwriting
-n 5 Is the number of times the operation should be performed (in this case five)

The shred command overwrites zeros and/or random data on top of the file, the more times you do this the more difficult it will be to recover.  It then renames the file several times to overwrite the filesystem record.

Based on the output of strings the data in fake2.txt the file is unreadable but there look to be traces of its existence on the filesystem.  I see some references to it in the strings output but I don't see any of the data I had input in the file.  I see references to 0000, 00000, etc. whcih were the titles shred used to rename the file to overwrite the filesystem record.  That leads me to believe it would be very difficult to recover the original file from the filesystem or any of its data but someone could tell that there was once a file called fake2.txt on the system.
```
shred: fake2.txt: pass 1/6 (random)...
shred: fake2.txt: pass 2/6 (ffffff)...
shred: fake2.txt: pass 3/6 (random)...
shred: fake2.txt: pass 4/6 (000000)...
shred: fake2.txt: pass 5/6 (random)...
shred: fake2.txt: pass 6/6 (000000)...
shred: fake2.txt: removing
shred: fake2.txt: renamed to 000000000
shred: 000000000: renamed to 00000000
shred: 00000000: renamed to 0000000
shred: 0000000: renamed to 000000
shred: 000000: renamed to 00000
shred: 00000: renamed to 0000
shred: 0000: renamed to 000
shred: 000: renamed to 00
shred: 00: renamed to 0
shred: fake2.txt: removed

sudo strings /dev/xvdb1
/mnt/newworld
vEH3
lost+found
file.txt
temp.txt
folder
data
vEH3
vEH3
vEH3
vEH3
vEH3
lost+found
file.txt
temp.txt
folder
data
fake1.txt
/mnt/newworld
vEH3
lost+found
file.txt
temp.txt
folder
data
fake1.txt
fake2.txt
i^'E
lost+found
file.txt
temp.txt
folder
data
fake1.txt
fake2.txt
.fak1.txt.swp
/mnt/newworld
vEH3
i^'E
f%L4
lost+found
file.txt
temp.txt
folder
data
fake1.txt
fake2.txt
.fak1.txt.swp
fak1.txt
lost+found
file.txt
temp.txt
folder
data
fake1.txt
fake2.txt
fak1.txt
i^'E
/mnt/newworld
vEH3
i^'E
lost+found
file.txt
temp.txt
folder
data
fake1.txt
fake2.txt
i^'E
/mnt/newworld
vEH3
lost+found
file.txt
temp.txt
folder
data
fake1.txt
fake2.txt
.fake1.txt.swp
/mnt/newworld
vEH3
lost+found
file.txt
temp.txt
folder
data
fake1.txt
fake2.txt
.fake1.txt.swp
fake1.txt~
/mnt/newworld
vEH3
lost+found
file.txt
temp.txt
folder
data
fake1.txt
fake2.txt
/mnt/newworld
vEH3
lost+found
file.txt
temp.txt
folder
data
fake1.txt
fake2.txt
.fake2.txt.swp
/mnt/newworld
vEH3
/mnt/newworld
vEH3
lost+found
file.txt
temp.txt
folder
data
fake1.txt
fake2.txt
/mnt/newworld
vEH3
lost+found
file.txt
temp.txt
folder
data
fake2.txt
/mnt/newworld
vEH3
/mnt/newworld
vEH3
lost+found
file.txt
temp.txt
folder
data
000000000
lost+found
file.txt
temp.txt
folder
data
00000000
lost+found
file.txt
temp.txt
folder
data
0000000
lost+found
file.txt
temp.txt
folder
data
000000
lost+found
file.txt
temp.txt
folder
data
00000
lost+found
file.txt
temp.txt
folder
data
0000
lost+found
file.txt
temp.txt
folder
data
lost+found
file.txt
temp.txt
folder
data
lost+found
file.txt
temp.txt
folder
data
lost+found
file.txt
temp.txt
folder
data
/mnt/newworld
vEH3
<ke*
vEH3
vEH3
b0nano 6.2
ubuntu
ip-10-0-0-25
fake2.txt
random info about me
b0VIM 8.2
ubuntu
ip-10-0-0-25
/mnt/newworld/fake1.txt
utf-8
U3210
#"! 
fake information about me...stuff.
text
temp
```

## Extra Credit Answers:

1. Commands used: sudo fallocate -l 2GB reservedDisk
2. Explanation: allocated 2GB of disk using the '-l' flag and size with '2G'.  Named the reserved file as 'reservedDisk'.  Verified using 'ls -lh'.
3. Commands used: sudo mke2fs -t ext4 reservedDisk, lsblk
4. Commands used: sudo mkdir /mnt/vfs, sudo mount reservedDisk /mnt/vfs, lsblk -o PATH,FSTYPE,MOUNTPOINT,SIZE /dev/loop10
```
PATH        FSTYPE MOUNTPOINT  SIZE
/dev/loop10 ext4   /mnt/vfs    1.9G
```
