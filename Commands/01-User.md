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
