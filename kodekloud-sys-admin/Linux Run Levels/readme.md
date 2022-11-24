# TASK

New tools have been installed on the app server in Stratos Datacenter. **Some of these tools can only be managed from the graphical user interface.** Therefore, there are requirements for these app servers.

On `all App servers` in Stratos Datacenter change the default runlevel so that they can boot in `GUI (graphical user interface)` by default. **Please do not try to reboot these servers**

# SOLUTION

There are 7 runlevels defined in any Linux machine, which are as follows:

```
0 System Halt

1 Single User Mode

2 Multi User Mode without networking

3 Multi User Mode with networking

4 Not Used/Special purpose

5 Multi User Mode with GUI

6 System Reboot
```

How to change the runlevel

```bash
# ssh into the remote server
shh <user>@<sever>

# if you are on a machine that doesn't use systemd

# use any of the 2 commands to check the current level
sudo runlevel
# or
sudo who -r

# use any of the 2 commands to set the run level
sudo telinit 5
# or
sudo init 5

# confirm if it has changed
sudo who -r
# or
sudo runlevel

# this is the file that handles setting of runlevel. run the command bellow to display its content
cat /etc/inittab

# inittab is no longer used when using systemd.
#
# ADDING CONFIGURATION HERE WILL HAVE NO EFFECT ON YOUR SYSTEM.
#
# Ctrl-Alt-Delete is handled by /usr/lib/systemd/system/ctrl-alt-del.target
#
# systemd uses 'targets' instead of runlevels. By default, there are two main targets:
#
# multi-user.target: analogous to runlevel 3
# graphical.target: analogous to runlevel 5
#
# To view current default target, run:
# systemctl get-default
#
# To set a default target, run:
# systemctl set-default TARGET.target

# use this command for machines that use systemd

# get the current default runlevel
systemctl get-default

# set the run level to use graphical user interface
sudo systemctl set-default graphical.target

# check if the default runlevel has changed
systemctl get-default
```
