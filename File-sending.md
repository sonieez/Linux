<h2>SFTP</h2>

<h3>Connecting to SFTP</h3>

In Powershell (windows) :
   ```bash
   stfp -P (port number) user1@(ip address)
   ```
   SFTP should be connected.

❗If you write any linux command  with extra 'l' front of it, it will apply that command for Windows:
```bash
lpwd   #Local working directory: c:\windows\system32
pwd    #Remote working directory: /home/user1
```
<hr>

<h3>1) Sending a file from Windows to Linux (<i>put</i>) </h3>

1) In Powershell(windows), find/create the file to send. For example, we want to send public key (from ssh):
   ```bash
   lcd ~
   lcd .\.ssh\    #changing directory to ssh
   lls            #we should see public key file (id_ed25519.pub)
   ```
3) Sending file to `/tmp` folder:
   ```bash
   put id_ed25519.pub /tmp
   ```
File is sent. We should see the file in `/tmp` folder in Linux.

<hr>

<h3>2) Sending a file from Linux to Windows (<i>get</i>) </h3>

1) In Linux bash, enter a user and create/find the file to send.
   ```bash
   su - user1

   touch /tmp/file1
   ```
2) In Powershell(windows), open the folder you want to save the file. For example, `ssh` folder:
   ```bash
   lcd ~
   lcd .\.ssh\
   ```
3) Get the file from `/tmp` folder:
   ```bash
   get /tmp/file1
   ```
File is sent. We should see the file in `ssh` folder in Windows.

<hr>

<h2>SCP</h2>

In SCP sending, we use Powershell (to send from Linux to Windows and vice versa).
First, we need to open the folder. For example, `ssh` folder:
```bash
cd ~
cd .\.ssh\
```

<h3>1) Sending a file from Windows to Linux</h3>

For example, we want to send `file2.docx` from `ssh` folder to `/tmp` folder:
```bash
scp -P (port number) ./file2.docx user1@(ip address):/tmp
```
File is sent. We should see the file in `/tmp` folder in Linux.
<hr>

<h3>2) Sending a file from Linux to Windows</h3>

For example, we want to send `file2` from `/tmp` to folder `ssh`:
```bash
scp -P (port number) user1@(ip address):/tmp/file2 .
```
File is sent. We should see the file in `ssh` folder in Windows.
