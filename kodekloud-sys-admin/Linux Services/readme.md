# TASK

As per details shared by the development team, the new application release has some dependencies on the back end. There are some packages/services that need to be installed on all app servers under `Stratos Datacenter`. As per requirements please perform the following steps:

1. Install `cups` package on all the application servers.

2. Once installed, make sure it is enabled to start during boot.

# SOLUTION

```bash
# ssh into the server
ssh tony@172.16.238.10

# run this command to see the linux distro - determins the package manager
cat /etc/\*-release

# if on CentOS/RHEL
sudo yum -y install cups

# if on Ubuntu/Debian
sudo apt -y install cups

# check the status of the installed service
sudo systemctl status cups.service

# if the service is not running, then run this
sudo systemctl start cups.service

# run this command to enable the service auto start up on reboot
sudo systemctl enable cups.service
```
