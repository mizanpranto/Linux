# Linux
Details about Linux and Command

 

<details>
  <summary>Basic Linux Tasks </summary>
  
## The CLI (Command-Line Interface)
● In Linux, users interact with the system through text commands entered at a prompt.
● The CLI presents a command prompt, and users enter commands to interact with the system.



</details>




<details>
  <summary style="color: blue;">Managing Users and Groups </summary>
  
## Assume Superuser Privileges

<h3 style="color: green;"> User Accounts </h3>

● Accounts represent users and services in Linux. <br>
● User accounts have attributes like passwords, group memberships, comments, etc.<br>
● Three types of accounts: root (superuser), standard user, and service accounts.<br>

<h3> Superuser</h3>

● Root account serves as the local administrator and security context for some applications. <br>
● Logging in directly as the root user is discouraged due to its extensive privileges.<br>
● "Principle of Least Privilege" suggests giving users the minimum necessary access for their tasks. <br>

<h3> The su Command </h3>

● Used to switch between user identities, allowing users to act as root.<br>
● The <b> su - </b> command launches a new shell as the target user.<br>
● The syntax is <b> su [-] [user name] </b>.<br>

<h3> The sudo Command </h3>

● Delegates specific commands to users, avoiding granting full root privileges. <br>
● Configuration is done in the <b> /etc/sudoers </b> file using the visudo editor.<br>
● The syntax is <b> sudo [options] {command} </b>.<br>

<h3>The sudoedit Command</h3>

● Enables users to edit files with their credentials, even if the file requires root privileges. <br>
● Must be configured in the <b> /etc/sudoers file </b>.<br>
● The syntax is <b>sudoedit [options] {file name}</b>.<br>

<h3>The visudo Command</h3>

● Used to edit the <b> /etc/sudoers </b> file securely to avoid syntax errors.<br>
● Syntax: <b>visudo [options] </b>.<br>


<h3>The wheel Group</h3>

● Many Linux distributions disable the root account for users and grant administrative privileges through the wheel group.<br>
● Members of the wheel group can use sudo to perform administrative tasks.<br>
● Membership in the wheel group should be carefully controlled.<br>




## Create, Modify, and Delete Users


<h3>The useradd Command</h3>

● Used for creating user accounts and configuring basic settings.<br>
● Default settings for the account are stored in /etc/login.defs.<br>
● Home directories are created under /home by default.<br>
● The useradd command does not set a password by default.<br>
● Syntax: useradd [options] [user name].<br>


<h3>The passwd Command</h3>

● Used for setting or resetting user passwords.<br>
● Users can change their passwords themselves using this command.<br>
● Also used to set the initial password when creating an account.<br>
● Syntax: passwd [user name].<br>


<h3> The /etc/passwd File</h3>

● Stores user account information.<br>
● Contains fields: User name, Password (usually 'x'), User ID, Group ID, Comment (full name), Home directory, and Login shell.<br>
● Properly edited using user management commands, not manual editing.<br>


<h3>The /etc/shadow File</h3>

● Modern storage location for hashed passwords and additional account info.<br>
● Only root has access to its content for enhanced security.<br>
● Prevents users from accessing each other's password hashes.<br>


<h3>The /etc/shadow File Format</h3>
● Fields include User name, Password hash, Days since password changed (from 01-01-1970), Days before password must be changed, Days until user is warned to change password, Days after password expires for account disablement.<br>


## Create, Modify, and Delete Groups


<h3>Group Accounts</h3>

● Groups associate user accounts with similar security requirements.<br>
● Simplify administrative tasks and resource access.<br>
● Represented by a Group ID (GID).<br>
● Users can be members of multiple groups.<br>

<h3>The /etc/group File</h3>

● Stores group information.<br>
● Contains fields: Group name, Password (usually 'x'), Group ID (GID), Group list (members).<br>
● Properly edited using group management commands, not manual editing.<br>

<h3>The groupadd Command</h3>

● Creates a group.<br>
● By default, the group has no members and no password.<br>
● Syntax: groupadd [options] [group names].<br>

<h3>The groupmod Command</h3>

● Used to modify group attributes.<br>
● Can change the group's name or GID.<br>
● Syntax: groupmod [options] [group names].<br>

<h3>The groupdel Command</h3>
● Deletes groups from the /etc/group file.<br>
● Does not delete user accounts that are members of the group.<br>
● Exercise caution when deleting groups.<br>


## Query Users and Groups

<h3>whoami Command:</h3>
● whoami displays the current user's name.<br>
● Useful for checking the user you're logged in as.<br>

<h3>who Command:</h3>

● who provides details about users currently logged into the system.<br>
● Shows user names, system names, and login times.<br>
● Use -u option to see how long users have been idle.<br>

<h3>w Command:</h3>
● w displays details of currently logged-in users and their activities.<br>
● Includes user names, terminal, login time, and current activities.<br>
● Great for tracking user activity in real-time.<br>

<h3>last Command:</h3>

● last shows login/logout history, time, and date for users.<br>
● Retrieves data from /var/log/wtmp. ● Can filter users or terminals using options.<br>

<h3>id Command:</h3>
● id displays user ID (UID) and group ID (GID) information.<br>
● Without options, it shows info for the currently logged-in user.<br>
● Specify a username to view information for other users.<br>



## Configure Account Profiles

<h3>.bashrc File:</h3>

● Located in the user's home directory.<br>
● Customizes a user's environment.<br>
● Used for aliases, environment variables, and customizing the command prompt.<br>
● User-specific and hidden (prefixed with a dot).<br>

<h3>.bash_profile File:</h3>

● Provides shell configuration for the initial login environment.<br>
● Only read during the first login.<br>
● User-specific, not applied to all shells.<br>
● Default .bash_profile can be set in the /etc/skel directory.<br>

<h3>/etc/skel/ Directory:</h3>

● Contents copied to new users' home directories.<br>
● Used for configuring initial settings for new users.<br>
● Changes made after user creation won't affect existing users.<br>

<h3>/etc/profile File:</h3>

● Provides system-wide environment variables.<br>
● Read during initial login for all users.<br>
● Global settings for Bash shell.<br>
● User-specific settings are pulled from the .profile file in the home directory.<br>

<h3>/etc/profile.d/ Directory:</h3>

● Storage for scripts to set system-wide variables.<br>
● Recommended for setting environment variables.<br>

<h3>/etc/bashrc File:</h3>
● Provides system-wide Bash settings.<br>




</details>






<details>
  <summary style="color: blue;" >Managing Permissions and Ownership </summary>
  

## Modify File and Directory Permissions


<h3>ls -l Command:</h3>

● Lists files and directories with permission information.<br>
● Displays columns with permission string, number of links, owner, group, size, date, and name.<br>
● Permissions are categorized into owner, group, and others.<br>

<h3>Permission Attributes:</h3>

● Read (r): Access and view files or list directory contents.<br>
● Write (w): Save changes to files or create/rename/delete files in directories.<br>
● Execute (x): Run files or access directories and perform tasks (e.g., search).<br>

<h3>Permission Contexts:</h3>

● Owner (u)<br>
● Group (g)<br>
● Other (o)<br>

<h3>Permission String:</h3>

● Displays file type (d for directory, - for file).<br>
● Followed by owner, group, and other permissions.<br>
● Plus (+) and period (.) represent SELinux security context.<br>

<h3>chmod Command:</h3>

● Used to modify file or directory permissions.<br>
● Syntax: chmod [options] {mode} {file/directory name}. ● Supports options like -c, -f, -v, -R for recursive changes.<br>

<h3>Symbolic Mode:</h3>

● Uses symbolic components: u/g/o/a, +/-/=, r/w/x.<br>
● Examples: chmod u+rw,g+rw myfile, chmod a+x script.<br>

<h3>Absolute Mode:</h3>

● Uses octal numbers (base-8) to specify permissions.<br>
● Example: chmod 755 file (owner: rwx, group: rx, others: rx).<br>


<h3>Three-Digit and Four-Digit Modes:</h3>

● Commonly represented as three digits: user/group/others.<br>
● May also use four digits for advanced permissions (0 for none).<br>
● Example: 0666 (rw-rw-rw-).<br>




## Modify File and Directory Ownership


<h3>Ownership:</h3>

● Ownership determines who can apply and modify permissions on a file or directory.<br>
● The owner of a file or directory is the user who created it.<br>
● By default, only the owner (or superuser) can change the permissions of an object.<br>

<h3>chown Command:</h3>

● Used to change the owner, group, or both for a file or directory.<br>
● Syntax: chown {user name} {file/directory name}, chown {user name}:{group name} {file/directory name}, etc.<br>
● -R option enables recursive ownership changes in a directory structure.<br>

<h3>chgrp Command:</h3>

● Used to change the group ownership of a file or directory.<br>
● Syntax: chgrp {group name} {file/directory name}.<br>




## Configure Special Permissions and Attributes

<h3>Special Permissions:</h3>

● Special permissions are used when normal permissions are not enough.<br>
● They allow users to execute files with the privileges of the file's owner or group temporarily.<br>

<h3>SUID and SGID Permissions:</h3>

● SUID (Set User ID) allows users to execute a file with the privileges of the owner.<br>
● SGID (Set Group ID) allows users to execute a file with the privileges of the group owner.<br>
● These permissions are set using chmod and are indicated by "s" in the execute position.<br>

<h3>Sticky Bit:</h3>

● Sticky bit ensures that only the owner or root can delete a file or directory.<br>
● Set using chmod and indicated by "t" or "T" (if execute permission is not set) in the execute position.<br>

<h3>File Attributes:</h3>

● File attributes allow you to customize the system's interaction with files.<br>
● Examples include read-only, automatic compression, saving when deleted, and immutability.<br>

<h3>Immutable Flag:</h3>

● The immutable flag prevents files from being modified, even by the root user.<br>
● Set with chattr and shown as "i" in file attributes.<br>

<h3>Access Control Lists (ACLs):</h3>

● ACLs allow for more granular control over permissions beyond traditional owner and group.<br>
● getfacl retrieves ACL information, and setfacl modifies ACLs.<br>
● ACLs are formatted as "u:{user}:{permissions}" for users and "g:{group}:{permissions}" for groups.<br>



## Troubleshoot Permissions Issues

<h3>Troubleshooting Models:</h3>

● Troubleshooting involves recognizing, diagnosing, and resolving problems efficiently.<br>
● Various troubleshooting models exist, and they aim to help you address problems systematically.<br>
● A common troubleshooting model includes identifying the problem, establishing a theory of probable cause, testing the theory, planning a solution, implementing it, verifying system functionality, and documenting the process.<br>

<h3>Permissions Troubleshooting:</h3>

● When facing permissions issues, verify object permissions and ownership using the ls -al command.<br>
● Ensure users have the necessary permissions and do not have access beyond what they should.<br>
● Check for the immutable flag, SUID permissions for executables, and sticky bits on directories.<br>
● Ensure correct owner and owning group settings.<br>
● Set the SGID permission on a directory to make new files inherit its group ownership.<br>
● Use groups {user name} to check a user's group membership.<br>
● Modify group membership when needed to grant or restrict access to specific users.<br>

Remember that following a structured troubleshooting approach is essential for efficiently identifying and resolving permissions issues. The ls -al command is your first tool for checking permissions and ownership, and you can use various other commands and techniques to address specific issues.


 
</details>





<details>
  <summary style="color: blue;">Managing Storage </summary>
  

## Create Partitions

● Setting XFS file system labels: Use the command xfs_admin -L {label name} /dev/{device name}{partition number}. <br>
● Partitions: Divisions of storage drives that act as separate logical drives, enhancing data organization. Partitions need formatting and file system assignment.<br>
● Partition Tables: Used to identify partitions; stored in the drive. Partition size cannot exceed free space.<br>
● Types of Partitions: Three types - Primary (one file system or logical drive, e.g., boot partition), Extended (contains logical drives), Logical (created within an extended partition, no set limit but typically limited to 12 per drive).<br>
● Swap Space: A partition for out-of-memory situations, typically twice the RAM capacity.<br>
● fdisk Utility: Menu-driven tool for partition management, supporting DOS and Linux partition tables.<br>
● fdisk Syntax: fdisk [options] {device name}<br>
● GNU Parted: Useful for creating, destroying, and resizing partitions.<br>
● GNU Parted Syntax: parted [options] {device name}<br>
● partprobe Command: Updates the kernel with changes in the partition table without rebooting.<br>
● partprobe Syntax: partprobe [options] [device name]<br>
● mkfs Command: Builds a Linux file system on a device or partition.<br>
● mkfs Syntax: mkfs [options] {device name}<br>
● fstab File: Stores information on storage devices and partitions to specify where and how partitions should be mounted.<br>
● /dev/ Directory: Contains files representing and supporting attached devices, following naming conventions.<br>
● /dev/disk/by- Identifiers: Persistent naming schemes like by-id, by-path, and by-uuid used to identify devices more predictably.<br>



## Manage Logical Volumes

<h3>Device Mapping:</h3>

● Device mapping is the process of abstracting physical storage devices into virtual storage devices.<br>
● Linux uses the device mapper to create virtual devices and manage data transfer between virtual and physical devices.<br>
● Device mapper is used for tasks like volume encryption and integrity checking services.<br>

<h3>DM-Multipath:</h3>

● DM-Multipath is a Linux kernel feature that enhances redundancy and performance for block storage devices.<br>
● It uses the device mapper to provide multiple I/O paths between the CPU and storage devices.<br>
● If one path fails, DM-Multipath switches to another available path, ensuring device availability for reading and writing.<br>

<h3>mdadm Command:</h3>

● mdadm is a tool for managing software-based RAID (Redundant Array of Independent Disks) arrays.<br>
● RAID arrays store data across multiple physical storage devices, creating a single virtual storage device.<br>
● mdadm allows the creation, management, and monitoring of RAID arrays.<br>

<h3>Logical Volume Manager (LVM):</h3>

● LVM is an application of the device mapper that maps physical devices and partitions into virtual containers called volume groups.<br>
● Volume groups contain one or more logical volumes, which become the storage devices.<br>
● LVM advantages include dynamic volume operations, easier management, mapping across multiple physical devices, and creating snapshots.<br>

<h3>/dev/mapper/ Directory:</h3>

● Contains all logical volumes managed by LVM.<br>
● Logical volumes are typically formatted as /dev/mapper/<volume group name>- <logical volume name>.



<h3>LVM Tools:</h3>

● LVM tools are categorized into physical volume (PV) tools, volume group (VG) tools, and logical volume (LV) tools.<br>
● PV tools include pvscan, pvcreate, pvdisplay, pvchange, pvs, pvck, and pvremove.<br>
● VG tools include vgscan, vgcreate, vgdisplay, vgchange, vgs, vgck, vgrename, vgreduce, vgextend, vgmerge, vgsplit, and vgremove.<br>
● LV tools include lvscan, lvcreate, lvdisplay, lvchange, lvs, lvrename, lvreduce, lvextend, lvresize, and lvremove.<br>


## Mount File Systems

<h3>Mount Points:</h3>

● A mount point is an access point to information stored on a local or remote storage device.<br>
● It is typically an empty directory where a file system is loaded or mounted to make the data accessible.<br>
● If the directory already has content, it becomes invisible to users until the mounted file system is unmounted.<br>

<h3>The mount Command:</h3>

● The mount command is used to load a file system to a specified directory to make it accessible to users and applications.<br>
● You need to specify both the device to mount and the desired mount point.<br>
● Mount options, such as auto, noauto, nouser, user, exec, noexec, ro, rw, sync, and async, can be specified.<br>
● These options are often included in the /etc/fstab file for automatic mounting during system startup.<br>

<h3>Binaries:</h3>

● Binaries are source code compiled into executable programs or files readable by the computer system.<br>


<h3>The umount Command:</h3>

● The umount command is used to unmount a file system after it has been mounted.<br>
● The file system must not be in use when unmounting.<br>
● Common umount command options include -f (force unmounting despite issues), -l(perform a "lazy" unmount), -R (recursively unmount directories), -t {fs type}(unmount specific file system types), -O {mount options} (unmount file systems with specified options in /etc/fstab), and --fake (test unmounting without actually performing it).<br>


## Manage File Systems

<h3>The /proc/mounts File:</h3>

● Lists the status of all currently mounted file systems in a format similar to fstab. ● Represents the status of mounted objects as reported by the Linux kernel.<br>
● Used to obtain details about currently mounted file systems.<br>

<h3>The mtab File:</h3>

● Similar to /proc/mounts, it reports the status of currently mounted file systems.<br>
● /proc/mounts is typically more accurate and up-to-date.<br>

<h3>The /proc/partitions File:</h3>

● Contains information about each partition currently attached to the system.<br>
● Provides information like major, minor, number of blocks, and partition names.<br>

<h3>The lsblk Command:</h3>

● Displays information about all block storage devices available on the system.<br>
● Provides details such as names, major and minor numbers, size, device type, and mount points.<br>

<h3>The blkid Command:</h3>

● Similar to lsblk, it prints each block device in a flat format and includes additional information like device/partition UUID and file system type.<br>
● Use lsblk -f for additional information.<br>

<h3>Tools for Managing Ext File Systems:</h3>

● Tools for managing ext file systems, such as ext2, ext3, and ext4, include e2fsck, resize2fs, tune2fs, and dumpe2fs.<br>

<h3>The fsck Command:</h3>

● Checks the integrity of a file system.<br>
● File system errors are usually caused by power failures, hardware failures, or improper shutdown.<br>
● Unmount the file system before scanning with fsck.<br>


<h3>The resize2fs Command:</h3>

● Enlarges or shrinks an ext2/3/4 file system on a device.<br>
● Must unmount the file system before shrinking it.<br>


<h3>The tune2fs Command:</h3>

● Configures tunable parameters associated with an ext2/3/4 file system.<br>
● Parameters include reserved blocks, mount checks, time intervals, and more.<br>

<h3>The dumpe2fs Command:</h3>

● Dumps ext2, ext3, and ext4 file system information, including superblock and block group information.<br>
● Useful for troubleshooting faulty file systems.<br>

<h3>XFS Tools:</h3>

● Tools for working with the XFS file system include xfs_info, xfs_admin, xfs_metadump, xfs_growfs, xfs_copy, and xfs_repair.<br>



## Navigate the Linux Directory Structure



<h3>Types of Files:</h3>

● Linux file system includes regular files (text, executables), directories, special files (block or character), links, domain sockets, and named pipes.<br>
● Represented by letters in the ls -l command output (d for directories, b/c for special files, l for links, s for domain sockets, p for named pipes).<br>

<h3>The file Command:</h3>

● Used to determine the type of a file.<br>
● Syntax: file [options] {file names}.<br>

<h3>File Naming Conventions:</h3>

● File names can be up to 255 bytes on ext4 filesystems.<br>
● Avoid using NULL (\0) and forward slash (/) in file names.<br>
● Convention: demarcate words with hyphen or underscore for easier command-line management.<br>

<h3>Filesystem Hierarchy Standard (FHS):</h3>

● Standardizes file and directory names/locations for Linux distributions.<br>
● Root directory (/) at the top, followed by various standardized subdirectories (e.g., /bin, /etc, /home, /lib).<br>

<h3>Home Directory:</h3>

● Contains personal files specific to a user.<br>
● Root user's home directory is /root.<br>

<h3>Current Working Directory:</h3>

● Location you are accessing at a given time.<br>
● Represented by a single period (.).<br>
● Use pwd to display it.<br>

<h3>Parent Directory:</h3>

● Directory one level above the current working directory.<br>
● Represented by double period (..).<br>

<h3>Paths:</h3>

● Specify file/directory locations in the file system.<br>
● Absolute paths begin with a forward slash (/).<br>
● Relative paths are based on the current working directory and may include . (current directory) and .. (parent directory).<br>

<h3>File System Navigation Commands:</h3>

● cd: Change the current working directory.<br>
● ls: List files and directories.<br>
● pwd: Print the current working directory.<br>



## Troubleshoot Storage Issues

<h3>Symptom: Degraded Storage</h3>

● Degraded storage occurs when a storage drive in a RAID array has failed.<br>
● Depending on the RAID type, the system may still function with reduced performance.<br>
● The failed drive can be replaced to restore optimal performance.<br>

<h3>Symptom: Performance Issues</h3>

● Investigating storage performance issues begins with considering the technology in use.<br>
● Workstations may use SATA hard drives or SSDs, while servers typically use more <br>
efficient options like SCSI, SAS, or SSDs, often in RAID arrays.<br>
● Failing disks, controllers, or hardware components can cause performance problems.<br>

<h3>Symptom: Resource Exhaustion</h3>

● In a busy server, too many open files can lead to resource exhaustion, causing most Linux commands to fail.<br>
● Rebooting the server can temporarily resolve the issue.<br>
● The ulimit command can be used to adjust the available number of file descriptors.<br>

<h3>Symptom: Storage Integrity/Bad Blocks</h3>

● Traditional magnetic hard disk drives may develop bad blocks over time.<br>
● Bad blocks are sections of the disk that can't be read from or written to, and the file system marks them for exclusion.<br>
● Too many bad blocks can diminish performance and capacity, indicating a failing hard disk drive that should be replaced.<br>

<h3>Storage Space Tracking:</h3>

● df (disk free) command shows device free space, file system, total size, space used, percentage used, and mount point.<br>
● du (disk usage) command shows directory and file sizes, helping track space hogs.<br>
● The -h option makes the output more human-friendly (e.g., in GB).<br>

<h3>I/O Scheduling:</h3>

● I/O scheduling manages the order of input/output operations for block storage devices.<br>
● Different scheduler types are available, including deadline, cfq, and noop.<br> 
● Changing the scheduler can help optimize performance in specific situations.<br>

<h3>iostat Command:</h3>

● iostat generates CPU and device usage reports.<br>
● Use -d to specify device information.<br>
● Provides statistics like transfers per second, blocks read/written per second, and more.<br>

<h3>ioping Command:</h3>

● ioping tests device I/O latency in real-time, similar to the standard ping for network latency.<br>
● Useful for troubleshooting latency issues.<br>

<h3>Storage Quotas:</h3>

● Storage quotas allocate space to users.<br>
● Quotas can have soft limits, grace periods, and hard limits.<br>
● Exceeding soft limits during grace periods can lead to hard limits.<br>

<h3>Quota Management Commands:</h3>

● Commands like quotacheck, edquota, and setquota are used for quota management.<br>
● Activate quotas by editing the fstab file.<br>
● For XFS, use the xfs_admin utility to configure quotas.v

<h3>Quota Reports:</h3>

● Reports detail user/group storage usage, soft/hard limits, and more.<br>
● Use commands like repquota and quota for generating reports.<br>

<h3>Additional Storage Troubleshooting Techniques:</h3>

● Troubleshooting starts with basic checks like permissions and available storage.<br>
● Verify physical connections and system recognition of storage devices.<br>
● Check configuration files (e.g., /etc/fstab) and tools like fsck.<br>

<h3>Guidelines for Troubleshooting Storage Issues:</h3>

● Ensure devices are physically connected and powered.<br>
● Verify device recognition by the system.<br>
● Check configuration files for errors and reload them.<br>
● Confirm storage capacity and workload.<br>
● Use partprobe to scan for new storage devices and partitions.<br>


  
</details>






<details>
  <summary style="color: blue;">Managing Files and Directories - working </summary>
  
  Content for section 3 goes here.
</details>




<details>
  <summary style="color: blue;">Managing Kernel Modules</summary>
  
  Content for section 3 goes here.
</details>




<details>
  <summary style="color: blue;">Managing System Components</summary>
  
  Content for section 3 goes here.
</details>





<details>
  <summary style="color: blue;">Managing Devices</summary>
  
  Content for section 3 goes here.
</details>





<details>
  <summary style="color: blue;">Managing Networking</summary>
  
  Content for section 3 goes here.
</details>




<details>
  <summary style="color: blue;">Managing Packages and Software</summary>
  
  Content for section 3 goes here.
</details>




<details>
  <summary style="color: blue;">Securing Linux Systems</summary>
  
  Content for section 3 goes here.
</details>




<details>
  <summary style="color: blue;">Working with Bash Scripts</summary>
  
  Content for section 3 goes here.
</details>






<details>
  <summary style="color: blue;">Automating Tasks</summary>
  
  Content for section 3 goes here.
</details>




