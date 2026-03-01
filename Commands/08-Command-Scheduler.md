**Cron** is a time-based job scheduler in Linux. It allows users to automatically run commands or scripts at specified times and dates.

**Crond** service that runs the scheduler.

📍Check status of crond service:
```bash
sudo systemctl status crond
```
📍Cron job:

Each cron job consists of **5 stars**:
<ol>
  <li>Minute (0 - 59)</li>
  <li>Hour (0 - 23)</li>
  <li>Day of Month (1 - 31)</li>
  <li>Month (1 - 12)</li>
  <li>Day of Week (1 - 7)</li>
</ol>

❗`*****` --> Runs every minute (by default)

For example - Run a script every Monday at 8:00 AM:

`0 8 * * 1 /script.sh`

📍Cron tab:

A **crontab** (cron table) is a file that contains scheduled jobs:

✔️To view the crontab:
```bash
crontab -l
```

✔️To edit the crontab or add the new one:
```bash
crontab -e
```

✔️To remove the crontab:
```bash
crontab -r
```
