# TASK

There is a critical issue going on with the Nautilus application in Stratos DC. The production support team identified that the application is unable to connect to the database. After digging into the issue, the team found that `mariadb service` is down on the `database server`.

Look into the issue and fix the same.

# SOLUTION

```bash
# ssh into the db server
ssh peter@172.16.239.10

# check service status
systemctl status mariadb.service

# try starting the server - this will fail
sudo systemctl start mariadb.service

# check service status for logs
systemctl status mariadb.service

# check system journal for more logs
journalctl -xe

# Incase the other commands dont give you enough data to work with run
systemctl status mariadb.service -l

# Check journal for the mariadb service - this worked for me
# issues was the /var/lib/mysql dir doesn't have the correct user
journalctl -u mariadb.service

# list the dirs to see the current owner of the /var/lib/mysql dir
ls -l /var/lib

# change the owner and group to `mysql`
sudo chown mysql:mysql /var/lib/mysql

# start service again
sudo systemctl start mariadb.service

# check if service is running
systemctl status mariadb.service

# enable service to start everytime the server restarts.
sudo systemctl enable mariadb.service
```
