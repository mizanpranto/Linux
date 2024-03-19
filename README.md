# Linux
Details about Linux and Command

 

<details>
  <summary>Basic Linux Tasks </summary>
  
## The CLI (Command-Line Interface)
● In Linux, users interact with the system through text commands entered at a prompt.
● The CLI presents a command prompt, and users enter commands to interact with the system.



</details>




<details>
  <summary style="color: blue;">Managing Users and Groups - working on</summary>
  
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
● Default settings for the account are stored in /etc/login.defs. ● Home directories are created under /home by default.<br>
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






</details>


<details>
  <summary style="color: blue;" >Managing Permissions and Ownership - not started </summary>
  
  Content for section 3 goes here.
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




