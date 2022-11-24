# TASK

Some users of the monitoring app have reported issues with xFusionCorp Industries mail server. They have a mail server in Stork DC where they are using postfix mail transfer agent. Postfix service seems to fail. Try to identify the root cause and fix it.

# SOLUTION

```bash
# ssh into the mail server
ssh groot@172.16.238.17

# run this to see the error
# error = fatal: parameter inet_interfaces: no local interface found for ::1
systemctl status postfix.service -l



# open the postfix main.cf file and make the following change
# search for the line inet_interfaces = all
# And change it to:
# inet_interfaces = 127.0.0.1, 10.10.11.12 - 10.10.11.12 is your local IP address
sudo vi /etc/postfix/main.cf


# if you dont want to use IPv6 on the server
# comment out the line with `::1 ` from the file
sudo vi /etc/hosts

# start the service
sudo systemctl start postfix.service

# enable the service
sudo systemctl enable postfix.service

# confirm the service is running correctly
systemctl status postfix.service -l
```
