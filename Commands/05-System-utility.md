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
<hr>

📍Status of the last used command ( 0 --> successful, other than 0 --> error):
```bash
echo $?
```
<hr>

📍To find where is the command located:
```bash
whereis #command
```
<hr>

📍Type of shell:
```bash
echo $0
#-bash
```
