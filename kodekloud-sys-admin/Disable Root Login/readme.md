# QUESTION

After doing some security audits of servers, xFusionCorp Industries security team has implemented some new security policies. One of them is to disable direct root login through SSH.

Disable direct SSH root login on `all app servers in Stratos Datacenter`.

# SOLUTION

You have to perfom the operations below on all `app servers`

```bash
# connect to each server
ssh <user>@<ip address>

# open /etc/passwd file
sudo vi /etc/passwd

# change
# root:x:0:0:root:/root:/bin/bash to root:x:0:0:root:/root:/sbin/nologin

# open /etc/ssh/sshd_config file then uncomment (if it is commented) the directive `PermitRootLogin` and set its value to `no`
sudo vim /etc/ssh/sshd_config

# PermitRootLogin no

# restart the sshd service
sudo systemctl restart sshd
```
