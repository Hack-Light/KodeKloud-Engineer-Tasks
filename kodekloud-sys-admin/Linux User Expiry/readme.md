# TASK

A developer `mariyam `has been assigned Nautilus project temporarily as a backup resource. As a temporary resource for this project, we need a `temporary user` for `mariyam`. It’s a good idea to create a user with a set expiration date so that the user won't be able to access servers beyond that point.

Therefore, create a user named `mariyam` on the `App Server 3`. Set expiry date to `2021-04-15` in `Stratos Datacenter`. Make sure the user is created as per standard and is in lowercase.

# SOLUTION

```bash
# ssh into app server 3
shh banner@stapp03

# create user
sudo useradd mariyam -e 2021-04-15
```
