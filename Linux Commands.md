# Basic Linux Commands

* Displays information about files in the current directory.
```
ls
```
*  Displays the current working directory.
```
pwd
```
*  Creates a directory.
```
mkdir
```
*  To navigate between different folders.
```
cd
```
*  Removes empty directories from the directory lists.
```
rmdir
```
*  Moves files from one directory to another.
```
cp
```
*  Rename and Replace the files
```
mv
```
*  Delete files 
```
rm
```
*  Command to get basic information about the OS
```
uname
```
*  Find a file in the database.
```
locate
```
* Create empty files
```
touch
```
*  Create shortcuts to other files
```
ln 
```
*  Display file contents on terminal
```
cat
```
*  Clear terminal 
```
clear
```
*  Display the active processes in terminal
```
ps
```
*  Access manual for all Linux commands
```
man
```
*  Search for a specific string in an output
```
grep
```
*  Display active processes on the terminal
```
echo
```
*  download files from the internet
```
wget
```
* Create or update passwords for existing users/Outputs username
```
whoami
```
*  sort the file content
```
sort
```
*  Check the details of the file system
```
df
```
*  Check the lines, word count, and characters in a file using different options 
```
wc
```
* Changes file permissions
```
chmod
```
* Runs an executable
```
./
```
* Exits the current shell session
```
exit
```
* Executes commands as superuser
```
sudo
```
* Shutdowns your machine
```
shutdown
```
* Extracts compressed ZIP files
```
unzip
```
* Terminates programs
```
kill
```
* Tests network connectivity
```
ping
```
* Efficient text editing
```
vim
```
* Shows a list of previous commands
```
history
```
* Changes user password
```
passwd
```
* Returns the full binary path of a program
```
which
```
* Inspects files interactively
```
less
```
* Displays last lines of a file
```
tail
```
* Displays first lines of a file
```
head
```
* Displays OS and hardware information
```
neofetch
```
* Searches for files that follow a pattern
```
find
```
* displays the file content with the line number
```
nl filename
```
### Edit File in Linux : 
* open the file with the Vi editor in the normal mode
```
vi filename
```

* Press the `ESC key` for `normal mode`.
* Press `i Key` for `insert mode`.
* Press `:q! keys` to exit from the editor without saving a file.
* Press `:wq! Keys` to save the updated file and exit from the editor.
* Press `:w test.txt` to save the file as test.txt
---
* displays the content of the file
```
cat filename
```
* Command to extract and compress files in Linux
```
tar
```
* Find the difference between two files
```
diff
```
* Allows you to check if two files are identical
```
cmp
```
* Combines the functionality of diff and cmp
```
comm
```
* Command for granting ownership of files or folders
```
chown
```
* Display network interfaces and IP addresses
```
ifconfig
```
* Locate the binary, source, and manual pages for a command
```
whereis
```
* Find what a command is used for
```
whatis
```
* View active processes live with their system usage
```
top
```
* Edits a file with a text editor.
```
nano, vi, and jed
```
* Finds, replaces, or deletes patterns in a file.
```
sed
```
* Finds and manipulates patterns in a file.
```
awk
```
* Reorders a file’s content.
```
sort
```
* Checks a file or directory’s storage consumption.
```
du
```
* prints information about your machine’s kernel, name, and hardware.
```
uname
```
* shows your system’s hostname.
```
hostname
```
* Manages system services.
```
systemctl
```
* Queries a domain’s IP address and vice versa.
```
nslookup
```
### Identifying and Mounting a Drive using the Linux Terminal :

* To Identify the USB drive
```
lsblk
```
* Create a directory to mount the USB drive into
```
sudo mkdir /media/pendrive
```
* Mounting the USB drive to the /media/pendrive directory using the mount command
```
syntax: sudo mount /path/to/drive /path/to/mountpoint.
> sudo mount /dev/sdb1 /media/pendrive
```
* Check the drive has been mounted by re-running
```
lsblk
```
* Unmount the drive using umount command
```
sudo umount /media/pendrive
```
* Check the drive is unmounted using
```
lsblk
```
## Formatting Disk Partition in Linux :
* There are three ways to format disk partitions using the mkfs command, depending on the file system type:
    * ext4
    * FAT32
    * NTFS
* The general syntax for formatting disk partitions in Linux is:
```
mkfs [options] [-t type fs-options] device [size]
```
#### Formatting Disk Partition with ext4 File System :
* Format a disk partition with the ext4 file system
```
sudo mkfs -t ext4 /dev/sdb1
```
* To verify the file system change
```
lsblk -f
```
#### Formatting Disk Partition with FAT32 File System :
* To format a disk with a FAT32 file system
```
sudo mkfs -t vfat /dev/sdb1
```
* To verify the file system change
```
lsblk -f
```
#### Formatting Disk Partition with NTFS File System :
* Format a disk partition with the NTFS file system
```
sudo mkfs -t ntfs /dev/sdb1
```
* To verify the file system change
```
lsblk -f
```
## Partition a Disk Using fdisk Command :
* To list all existing partitions
```
sudo fdisk -l
```
* Select the storage disk you want to create partitions
```
sudo fdisk /dev/sdb
```
>The /dev/sdb storage disk is open

* To Create a New Partition.
    * Run the  `n` command to create a new partition.
    * Select the partition number by typing the default number (2).
    * After that, you are asked for the starting and ending sector of your hard drive. It is best to type the default number in this section (3622912).
    * The last prompt is related to the size of the partition. You can choose to have several sectors or to set the size in megabytes or gigabytes. Type `+2GB` to set the size of the partition to 2GB.
    
* Write on Disk :
>The system created the partition, but the changes are not written on the disk.
* To write the changes on disk, run this command
```
w
```
* To Verify that the partition is created
```
sudo fdisk -l
```
#### Format the Partition
* To Format the Partition
```
sudo mkfs -t ext4 /dev/sdb1
```
#### Mount the Partition
>To begin interacting with the disk, need to create a mount point and mount the partition to it.

* Create a mount point by running the following command:
```
sudo mkdir -p /mt/sdb1
```
* After that, mount the partition by entering:
```
sudo mount -t auto /dev/sbd1 /mt/sdb1
```
* To Verify if partition is mounted 
```
df hT
```