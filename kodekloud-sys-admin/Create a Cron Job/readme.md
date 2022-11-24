# TASK

The Nautilus system admins team has prepared scripts to automate several day-to-day tasks. They want them to be deployed on all app servers in Stratos DC on a set schedule. Before that they need to test similar functionality with a sample cron job. Therefore, perform the steps below:

a. Install `cronie` package on `all Nautilus app servers` and start `crond` service.

b. Add a cron `*/5 * * * * echo hello > /tmp/cron_text` for root user.

# SOLUTION

Apply this solution to all `app servers`

```bash
# ssh into remote server
ssh <user>@<server.ip>

# check if cronie is running
sudo systemctl status cronie

# install it if it is not running
sudo yum install cronie

# check crond status
sudo systemctl status crond

# start crond service
sudo systemctl start crond

# confirm it is running
sudo systemctl status crond

# run this to create and register a cron job
sudo crontab -e

# view cron job
sudo crontab -l

# view cron jobs by the root user
sudo crontab -u root -l
```
