# TASK

The system admins team of xFusionCorp Industries has set up some scripts on jump host that run on regular intervals and perform operations on all app servers in Stratos Datacenter. To make these scripts work properly we need to make sure the thor user on jump host has password-less SSH access to all app servers through their respective sudo users (i.e tony for app server 1). Based on the requirements, perform the following:

Set up a password-less authentication from user thor on jump host to all app servers through their respective sudo users.

# SOLUTION

```bash
# confirm if there is any public key available
ls -al ~/.ssh/id_*.pub

# generate an SSH key pair
ssh-keygen -t rsa

# confirm if there is any public key available
ls -al ~/.ssh/id_*.pub

# if your remote server already has a .ssh/authorized_keys directory, run this
cat .ssh/id_rsa.pub | ssh tony@172.16.238.10 'cat >> .ssh/authorized_keys'

# your remote server already has a .ssh/authorized_keys directory

# connect to it using ssh
ssh <user>@<remote id address>

# create .ssh folder
mkdir .ssh

# create authorized_keys file
touch .ssh/authorized_keys

# check file permission
ls -al

# give folder and file the right permissions
chmod 700 .ssh
chmod 640 .ssh/authorized_keys

# exit remote sever
exit

# copy the public key to the remote server
cat .ssh/id_rsa.pub | ssh <user>@<remote.ip.address> 'cat >> .ssh/authorized_keys'

# try connecting again using ssh. you shouldn't be asked for a password
ssh <user>@<remote.ip.address>
```
