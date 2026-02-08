<h2>Step 1. Getting Port Number</h2>

1) Change user to *root* --> `su -`
2) Read(`cat`) or change(`vim`) PORT Number in `/etc/ssh/sshd_config`.

<h2>Step 2. Restarting SSH</h2>

1) Stopping firewall for ssh --> `systemctl stop firewalld.service`
2) `setenforce 0`
3) Restarting --> `systemctl restart sshd`

<h2>Step 3. Getting IP</h2>

`ip a` --> find the IP address

<h2>Step 4. Connecting with Password</h2>

1) Opening Powershell as Administrator in Windows
2) `ssh -p (port number) (username)@(ip address)`
3) Writing password of user and connecting.


<h2>Step 4. Connecting without Password</h2>

1) Opening Powershell as Administrator in Windows
2) Creating public/private key pair --> `ssh-keygen.exe` 
3) Opening file containing keys : `cd ~` --> `cd .\.ssh\` --> `explorer .`
4) Getting keys ( in /.ssh/id_ed25519) - two keys (public and private)
5) Copying Public key.
6) Opening Red hat bash and opening/creating a user.
7) Making directory to save the key --> `mkdir .ssh`
8) Writing public key in the file and saving --> `vim .ssh/authorized_keys` (`esc` + `:wq!`)
9) Trying again `ssh -p (port number) (username)@(ip address)`. It will connect without a password.

