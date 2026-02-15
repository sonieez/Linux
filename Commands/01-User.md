📍Switch to **root**:

```bash
su -
```

`su` means switching to another user <br>
`-` means login shell loads **root**'s environment

✔️ To write commands needing **root**s permission  <br>
✔️Requires root password
<hr>

📍Registering the system to Red Hat system:
```bash
sudo subscription-manager register
```
✔️Gets temporary root permission <br>
✔️Requires user's password

<hr>

📍Adding user:
```bash
useradd user1
passwd user1
#Password: ...
```
<hr>

📍To know which user is in use:
```bash
whoami
```
<hr>

📍ID of an user:
```bash
id user
```
We see different idetificators of an user:

✔️UID (user id)

Unique id of an user.

To change it:
```bash
usermod -u (number) user
```

✔️GID (group id):

Unique id of the *primary* group of the user. Every user has its own primary group by default.

To change it:
```bash
usermod -g group1 user
#changing user's primary group to group1

usermod -g (number) user
#changing user's primary group id
```

✔️Groups:

General groups that user is in. We can add, remove them.

Creating new group:
```bash
groupadd group1

gpasswd group1   #setting password for group1
```
Adding group to the user:
```bash
usermod -aG group1 user
```
Removing the group:
```bash
groupdel group1
```

✔️Type of the shell (available or not):

1) In use - `/bin/sh`
2) Not available - `/sbin/nologin`

To change it:
```bash
usermod -s /sbin/nologin user  #after this user won't be available

usermod -s /bin/sh user  #after this user can be used
```
<hr>

📍Creating a user with specific identificators:
```bash
useradd -u (number) -s /bin/sh -d /home/user4 user4
#creating user4 with specific user id, /bin/sh type of shell and making its home directory /home/user4
```
There are different options we can add to `useradd`.

<hr>

📍To see all users:
```bash
cat /etc/passwd
```

📍To see all users with passwords (encrypted):
```bash
cat /etc/shadow
```

📍PASSWORD information:

✔️In `/etc/shadow` file, after the passwords, we can see some numbers. For example, `20497:0:99999:7`:
<ul>
  <li> `20497` means that today is the 20497th day after the creation of Linux. </li>
  <li> `0` means that to change the password you need 0 day after the last change. </li>
  <li> `99999` means that password will expire after 99999 days --> never</li>
  <li> `7` means how many days before, the system will warn you for expiration.</li>
</ul>

✔️In `/etc/login.defs` file, we can see three of these parameters:
```bash
PASS_MAX_DAYS  99999
PASS_MIN_DAYS  0
PASS_WARN_AGE  7
```
We can change them in this file.

✔️To adjust these parameters, we can also use `passwd` command with its options (view `passwd --help`:
```bash
passwd -x 1000 -n 10 -w 5 user1
#changing parameter for user1 --> x-Maximum days, n-Minimum days, w-Warning days
```
✔️ We can manage password aging information for a user account with `chage` command an its options (view `chage ==help`):

With `chage`, we can:

1) Set minimum days between password changes:
   ```bash
   sudo chage -m (number) user1
   ```

2) Set maximum days before password expires:
   ```bash
   sudo chage -M (number) user1
   ```

3) Set warning days before expiration:
   ```bash
   sudo chage -W (number) user1
   ```

4) Set account expiration date:
   ```bash
   sudo chage -E 2026-12-31 user1
   ```

5) View current password aging settings:
   ```bash
   chage -l user1   #we can see minimum, maximum days for password change, warning days, last password change etc.
   ```
