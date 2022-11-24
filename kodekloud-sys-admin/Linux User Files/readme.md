# TASK

There was some users data copied on `Nautilus App Server 3` at `/home/usersdata` location by the Nautilus production support team in Stratos DC. Later they found that they mistakenly mixed up different user data there. Now they want to filter out some user data and copy it to another location. Find the details below:

On `App Server 3` find all `files (not directories)` owned by user `ammar` inside `/home/usersdata` directory and copy them all while keeping the folder structure (preserve the directories path) to `/official` directory.

# SOLUTION

```bash
# ssh into the app server 3
ssh banner@172.16.238.12

# list the folder content to see files and folders owned by ammar
ls -l /home/usersdata/

# run this to copy all files to oficial folder
sudo find /home/usersdata/ -type f -user ammar -exec cp --parents {} /official \;

# use this to inspect if your command worked
ls /official

ls /official/home

ls /official/home/usersdata/
```
