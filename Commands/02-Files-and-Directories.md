<img width="600" height="300" alt="image" src="https://github.com/user-attachments/assets/43937926-c8d9-4360-8735-db36ff5ad404" />
<hr>

📍Tree View of Files & Directories:
```bash
tree folder/
```

<hr>

📍Navigating between Files & Directories:

✔️Change to another directory
```bash
cd ..      #go one level up (previous directory)
cd ~       #go to HOME directory
cd /tmp    #go to /tmp directory
cd folder  #go to any folder
```
✔️Get your current location
```bash
pwd   #Print Working Directory
```

<hr>

📍Creating Files & Directories:

✔️Create a directory
```bash
mkdir folder1   
```
✔️Create a *hidden* directory
```bash
mkdir .folder2  
```
✔️Create a file
```bash
touch file1   
```
  ❗*To create multiple files by sequence:*
  ```bash
  touch file {10...20}  #file10, file11, ..., file20 will be created
  ```
  
✔️Create a *hidden* file 
```bash
touch .file2    
```

<hr>

📍Copying Files & Directories:

✔️Copy a file
```bash
cp file1 /folder1    #copying file1 into folder1   (folder1/file1)
```
✔️We can also rename the file while copying
```bash
cp file1 /folder2/file2   #copying file1 into folder2 as file2   (folder2/file2)
```
✔️Copy directory
```bash
cp -r folder1 /folder2    #copying folder1 into folder2 (folder2/folder1)
```

❗`-r` is mandatory for folders

<hr> 

📍Moving Files & Directories:

✔️Move
```bash
mv file5 folder1    #moving file5 into folder1
```
✔️We can also change the name of the file/directory with it
```bash
mv old-name new-name
```

<hr>

📍Removing Files & Directories:

✔️Delete a file
```bash
rm file1
```
✔️Delete a file WITH confirming
```bash
rm -i file1
#rm: remove regular empty file 'file1'? --> y/n
```
✔️Delete a directory (directory + things inside)
```bash
rm -r folder/
#rm: descend into directory 'folder/'? --> y/n
#rm: remove directory 'folder/folder1'? --> y/n
#rm: remove directory 'folder/folder2'? --> y/n
#rm: remove regular empty file 'folder/.file2'? --> y/n
#rm: remove directory 'folder/'? --> y/n
```
✔️Delete an empty directory (doesn't ask)
```bash
rmdir folder/
```
<hr>

📍Listing Files & Directories:
```bash
ls
```
✔️Types of listing
```bash
ls -l   #long format (permissions, owner, size, date, etc.)
ls -a   #hidden files (. files)
ls -la  #long+hidden combo

ls D*   #files starting with D (case-sensitive)

ls folder1/  #listing content of folder1
```
<hr>

📍Editing File Content:

1️⃣Writing inside of the file:
```bash
vim file1
```
✔️After writing, you need to press `Esc`, then write `:wq!` to save and exit

✔️To delete the row --> press `dd`.

✔️When we have multiple rows in the file, we can numerate rows (in the `esc` mode), by writing `:set number`. After that, we can access any row by simply typing the number `:5` (for example 5th row). 

2️⃣Overwriting:
```bash
echo hello > file1   
#file1 contains = hello

echo bye > file1
#file1 contains = bye  (hello is overwrited)
```

3️⃣Adding:
```bash
echo hello >> file1
#file1 contains = hello

echo bye >> file1
#file1 contains = hello bye
```
<hr>

📍Viewing File Content:

✔️Print entire file
```bash
cat file1
```
✔️Print entire file BUT in reverse order
```bash
tac file1
```
✔️Paging  (press `q` to quit)
```bash
more file1   #more content
less file1   #less content
```
✔️Parting
```bash
head file1    #beginning of the file1
tail file1    #end of the file1

head -n 5 file1    #first 5 rows of file1

head -n 5 file1 | tail -1   #last one row of the first 5 rows
```
❗`|`  Pipe = connects commands 

<hr>

📍Searching files:
```bash
grep
```
For example:

```bash
grep user1 /etc/passwd
#Search for lines containing user1 in /etc/passwd

cat /etc/passwd | grep user1
#Same as above, but using cat to feed the file
```

Searching Options:
```bash
grep ^root /etc/passwd       #Lines that start with “root”
grep root /etc/passwd        #Lines containing “root” anywhere
grep -w root /etc/passwd     #Lines where “root” is a whole word

grep bash$ /etc/passwd       #Lines ending with “bash” (usually login shell)
```

Context Options:
<ul>
  <li>-A (after) </li>
  <li>-B (before) </li>
  <li>-C (before and after) </li>
</ul>

```bash
grep ^root /etc/passwd -A 3     #Lines starting with root plus 3 lines after (A=after)

grep ^root /etc/passwd -B 1     #Lines starting with root plus 1 line before (B=before)

grep ^root /etc/passwd -C 5     #Lines starting with root plus 5 lines before & after (C=context)
```
<hr>

📍Directing errors (results) to files:

✔️Error:
```bash
2> error
#writes errors to error file
```
For example:
```bash
ls -l filee 2> error
#when filee does not exist, this command will give an error --> error is directed into the error file
```
❗We can direct results into `/dev/null` --> it won't be saved

📍Tailing file context:
```bash
tail -f file
```
✔️When we write something into the file (with >>), we can view it live in the terminal

<hr>

📍Archive and compress:

✔️Archiving files into one file:
```bash
tar cf archive.tar 1*
#Creates a tar archive named archive.tar containing all files that start with 1.
```
✔️Viewing archived files:
```bash
tar tf.archive.tar
#Lists all files inside archive.tar without extracting them.
```
✔️Compression (to bzip2, gzip, etc):
```bash
bzip2 file           #file.bz2
gzip archive.tar     #archive.tar.gz
```
