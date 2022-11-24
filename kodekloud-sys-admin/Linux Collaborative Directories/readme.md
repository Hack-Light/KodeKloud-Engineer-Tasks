# TASK

The Nautilus team doesn't want its data to be accessed by any of the other groups/teams due to security reasons and want their data to be strictly accessed by the devops group of the team.

Setup a collaborative directory `/devops/data` on `Nautilus App 1` server in `Stratos Datacenter`.

The directory should be group owned by the group `devops` and the group should own the files inside the directory. The directory should be `read/write/execute` to the group owners, and `others` should not have any access.

# SOLUTION

```bash
# ssh into the required server
ssh <user>@<ip address>

# list groups
groups

# make directory
sudo mkdir -p /devops/data

# confirm the directory creation
ls /devops

# create devops group (if doesn't exist already)
sudo groupadd devops

# change folder and children's group ownership to devops group
sudo chown :devops -R /devops

# confirm it worked
ls -l /

# give the group read, write, execute access
sudo chmod -R g+wrx /devops

# confirm it works
ls -l /

# remove all access from others
sudo chmod -R o-wrx /devops

# confirm it works
ls -l /
```
