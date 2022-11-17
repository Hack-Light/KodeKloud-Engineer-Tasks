# QUESTION

The system admins team of xFusionCorp Industries has noticed intermittent issues with DNS resolution in several apps . App Server 3 in Stratos Datacenter is having some DNS resolution issues, so we want to add some additional DNS nameservers on this server.

As a temporary fix we have decided to go with `Google public DNS (ipv4)`. Please make appropriate changes on this server.

# SOLUTION

```bash
# login into the system
ssh banner@stapp03

# view content of the config file
cat /etc/resolv.conf

# search stratos.xfusioncorp.com
# nameserver 127.0.0.11
# options ndots:0

# change nameserver 127.0.0.11 to nameserver 8.8.8.8 or nameserver 8.8.4.4
```
