✔️We can change IP address of a host:

1) Open the file `/etc/hosts` where hosts are saved and add new host:
   
   ```bash
   1.2.3.4    (domain name)
   ```
2) After we save that, when we send ping to that domain, nothing will be send:
   
   ```bash
   ping (domain name)
   ```

✔️We can change it back by simply entering `/etc/hosts` and delete what we wrote. It will go back how it was.
