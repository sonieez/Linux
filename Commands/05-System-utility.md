📍Reuse the last command:
```bash
!!
```
For example:
```bash
ls -l
#result
!!
#ls -l
#result again
```

📍Status of the last used command ( 0 --> successful, other than 0 --> error):
```bash
echo $?
```

📍To find where is the command located:
```bash
whereis #command
```

