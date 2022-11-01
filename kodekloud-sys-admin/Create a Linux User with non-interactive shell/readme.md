# QUESTION

The System admin team of xFusionCorp Industries has installed a backup agent tool on all app servers. As per the tool's requirements they need to create a user with a `non-interactive shell`.

Therefore, create a user named `rose` with a non-interactive shell on the `App Server 2`


# SOLUTION

```bash
# ssh into the required server
ssh steve@172.16.238.11

# get list of users
cut -d: -f1 /etc/passwd

# add user who cannot login
sudo adduser rose -s /sbin/nologin # or /bin/false

# get updated list of users
cut -d: -f1 /etc/passwd
```