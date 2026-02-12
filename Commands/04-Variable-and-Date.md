📍Creating a variable:
```bash
name=value
```

📍Printing:
```bash
echo $name    #value
echo name     #name
```
❗`$` reads the value of the variable

📍Printing with ' and " :
```bash
echo "$name ..."   #value ...
echo '$name ...'   #name ...
```

📍Printing Commands:
```bash
echo $PWD 
```

📍Local and Global Variables:

✔️Local variable:

Can be used only in the current shell.
```bash
name=S
```
Only in current user, if we write `echo $name` it will give us `S`.

✔️Global variable:

Can be used in other users and child processes.
1) Temporary:
   ```bash
   export surname=Z
   ```
2) Permanent:
   ```bash
   su - #change to root

   vim /etc/profile #add some global variable - export dep=IT
   ```
Global variables are seen by other users. So, if write `echo $soyad` or `echo $dep` in any user, it will use the global variables.

❗All the global variables can be seen with `env` command.

✔️We can write *script* using variable:
1) Writing script file (in user):
   ```bash
   vim script.sh
   ```
2) In the script file, we write:
   ```bash
   #!/bin/bash

   echo hi $name
   echo hi #surname
   ```
3) If we create global and local variables (in root's `/etc/profile`):
   ```bash
   name=S
   export surname=Z
   ```
4) If we read the user's script file:
   ```bash
   bash script.sh
   #result:
   #hi
   #hi Z
   ```
   Because, `name` variable isn't global variable, but `surname` is. 
<hr>

📍Date:
```bash
date   #Fri Feb 8...
```
✔️Printing date
```bash
echo 'date'    #date
echo `date`    #Fri Feb 8...
#or
echo $(date)   #Fri Feb 8...
```
