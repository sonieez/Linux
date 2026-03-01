📍Basic Linux Permissions:

✔️In Linux, every file and directory has permissions for three categories of users:
<ul>
  <li>User - u (owner)</li>
  <li>Group - g</li>
  <li>Other - o</li>
</ul>

✔️Each category has three types of permissions:

<ol>
  <li>r - Read - 4</li>
  <li>w - Write - 2</li>
  <li>x - Execute - 1</li>
</ol>

✔️`chmod` changes file or directory permission.

For example:
```bash
chmod 777 file1   #giving all permissions to all categories 7 = 4 + 2 + 1

chmod 754 file2
#All permissions to User --> 7 = 4 + 2 + 1
#Read and Execute permissions to Group --> 5 = 4 + 1
#Read permission to Others --> 4
```
Or we can use letters to manage permissions:
```bash
chmod u+x file3   #giving Execute permission to User

chmod u-x file3   #taking Execute permission from User

chmod g+w file4   #giving Write permission to Group
```
❗`+` sign adds permission and `-` sign takes permission back.

<hr>

📍Special Permissions:

✔️Linux also has three special permission bits:
<ul>
  <li>SUID (Set User ID) - 4 - (u+s)</li>
  
  →When SUID is set on an executable file, the program runs with the file owner's privileges, not the user who runs it.
  
  <li>SGID (Set Group ID) - 2 - (g+s)</li>

  →When SGID is set on an executable file, the program runs with the file's group privileges.

  →If SGID is set on a directory, new files created inside inherit the directory’s group.
  
  <li>Sticky Bit - 1 - (+t)</li>

  →When Sticky Bit is set, users can delete only their own files inside that directory. Even if others have write permission.
</ul>

✔️To add a special permission:
1) add the number before the basic permission:
   
   ```bash
   chmod 4777 file5  #giving SUID permission with all rwx permissions to file5

   chmod 2715 file6  #giving SGID permission with rwx--xr-x permission to file6

   chmod 1356 file7  #giving Sticky bit permission with -wxr-xrw- permission to file7
   ```
2) use letter combination for the permission:
   
   ```bash
   chmod u+s file8  #SUID permission
   chmod g+s file9  #SGID permission
   chmod +t file10  #Sticky bit permission
   ```

❗**Important**: 

If execution bit is missing but special bit is set, it shows as uppercase:
```bash
-rwSrwxrwx   #User doesn't have Execute permission --> SUID permission is S (uppercase)
-rwsrwxrwx   #user has Execute permission --> SUID permission is s (lowercase)

-rwxrwSrwx   #Group doesn't have Execution permission --> SGID permission is S
-rwxrwsrwx   #Group has Execution permission --> SGID permission is s

-rwxrwxrwT   #Others don't have Execution permission --> Sticky bit is T
-rwxrwxrwt   #Other have Execution permission --> Sticky bit is t
```
<hr>

📍Change Owner and Group:

```bash
chown (owner):(group) file

#For example:
chown user1:group1 file1
```

<hr>

📍User Mask:

✔️`umask` (user mask) is a Linux command that controls the default permissions of newly created files and directories.

✔️When you create a new file or directory, Linux gives it default permissions.
`umask` removes some of these permissions for security reasons.

❗So, umask does not add permissions — it **removes** permissions.

✔️Default permissions:
<ul>
  <li>Files --> 666 (rw-rw-rw-)</li>
  <li>Directories --> 777 (rwxrwxrwx)</li>
</ul>

✔️Formula:
`Default Permission - umask = Final Permission`

Example: 
```bash
umask 022

#Directories - 777-022=755 --> rwxr-xr-x
#Files - 666-022=644 --> rw-r--r--
```
Like that, umask will disappear after the terminal closes.

✔️To set the umask permanently:

<ul>
  <li>User-level:</li>
  
  ```bash
  vim .bashrc
  ```
  <li>System-wide:</li>

  ```bash
  vim /etc/profile
  ```
</ul>

<hr>

📍Attributes:
<ol>
  <li>+i --> immutable (can't modify or delete)</li>
  <li>+a --> append only </li>
</ol>

✔️To view the current attributes:
```bash
lsattr file1
```

✔️To add a new attribute or remove (change in total):
```bash
chattr +i file1
chattr +a file1

chattr -i file1
chattr -a file1
```
