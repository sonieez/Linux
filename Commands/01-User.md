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
useradd
```
