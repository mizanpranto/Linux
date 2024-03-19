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
  <summary style="color: blue;" >Managing Permissions and Ownership - working on </summary>
  

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
  <summary style="color: blue;">Managing Storage</summary>
  
  Content for section 3 goes here.
</details>






<details>
  <summary style="color: blue;">Managing Files and Directories</summary>
  
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




