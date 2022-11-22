# TASK

The system admins team of xFusionCorp Industries has set up a new tool on all app servers, as they have a requirement to create a service user account that will be used by that tool. They are finished with all apps except for `App Server 3`in Stratos Datacenter.

Create a user named `jim` in `App Server 3` without a home directory.

# SOLUTION

```bash
# ssh into the sever
ssh banner@172.16.238.12

# change to root user
sudo su -

# add user
useradd -M jim

```
