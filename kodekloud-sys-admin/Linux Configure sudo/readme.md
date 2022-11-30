# TASK

We have some users on all app servers in Stratos Datacenter. Some of them have been assigned some new roles and responsibilities, therefore their users need to be upgraded with sudo access so that they can perform admin level tasks.

- Provide sudo access to user `john` on all app servers.

- Make sure you have set up password-less sudo for the user.

# SOLUTION

```bash
ssh user@server

sudo su -

# Edit the sudoers file.

# The sudoers file is a file that administrators use to allocate system rights to users.

# It is recommended that you use the visudo command, rather than editing this file directly

sudo visudo


# Locate the line that contains includedir /etc/sudoers.d

# Below that line, add the following command:

john ALL=(ALL) NOPASSWD: ALL
```
