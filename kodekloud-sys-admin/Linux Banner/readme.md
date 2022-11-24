# TASK

During the monthly compliance meeting, it was pointed out that several servers in the Stratos DC do not have a valid banner. The security team has provided serveral approved templates which should be applied to the servers to maintain compliance. These will be displayed to the user upon a successful login.

Update the message of the day on all application and db servers for Nautilus. Make use of the approved template located at /home/thor/nautilus_banner on jump host

# SOLUTION

```bash

# copy the nautilus_banner into the remote servers using scp
scp -r /home/thor/nautilus_banner tony@stapp01:~/

scp -r /home/thor/nautilus_banner steve@stapp02:~/

scp -r /home/thor/nautilus_banner banner@stapp03:~/

# this would give an error because scp is not installed on the server
scp -r /home/thor/nautilus_banner peter@stdb01:~/

# bash: scp: command not found
# lost connection


# REPEAT THESE STEPS FOR ALL APP SERVERS


# ssh into app01 server
ssh tony@stapp01

# view the copied file
ls

# view the content of the nautilus_banner file
cat nautilus_banner

# ################################################################################################
#   .__   __.      ___      __    __  .___________. __   __       __    __       _______.        #
#        |  \ |  |     /   \    |  |  |  | |           ||  | |  |     |  |  |  |     /       |   #
#        |   \|  |    /  ^  \   |  |  |  | `---|  |----`|  | |  |     |  |  |  |    |   (----`   #
#        |  . `  |   /  /_\  \  |  |  |  |     |  |     |  | |  |     |  |  |  |     \   \       #
#        |  |\   |  /  _____  \ |  `--'  |     |  |     |  | |  `----.|  `--'  | .----)   |      #
#        |__| \__| /__/     \__\ \______/      |__|     |__| |_______| \______/  |_______/       #
#                                                                                                #
#                                                                                                #
#                                                                                                #
#                                                                                                #
#                                  # #  ( )                                                      #
#                                   ___#_#___|__                                                 #
#                               _  |____________|  _                                             #
#                        _=====| | |            | | |==== _                                      #
#                  =====| |.---------------------------. | |====                                 #
#    <--------------------'   .  .  .  .  .  .  .  .   '--------------/                          #
#      \                                                             /                           #
#       \_______________________________________________WWS_________/                            #
#   wwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwww                        #
# wwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwww                       #
#    wwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwww                         #
#                                                                                                #
#                                                                                                #
# ################################################################################################
# Warning! All Nautilus systems are monitored and audited. Logoff immediately if you are not authorized!

# move the content of nautilus_banner to /etc/motd
sudo mv nautilus_banner /etc/motd

# exit the remote server
exit

# login again and after a successful login you should see the banner
ssh tony@stapp01

# ################################################################################################
#   .__   __.      ___      __    __  .___________. __   __       __    __       _______.        #
#        |  \ |  |     /   \    |  |  |  | |           ||  | |  |     |  |  |  |     /       |   #
#        |   \|  |    /  ^  \   |  |  |  | `---|  |----`|  | |  |     |  |  |  |    |   (----`   #
#        |  . `  |   /  /_\  \  |  |  |  |     |  |     |  | |  |     |  |  |  |     \   \       #
#        |  |\   |  /  _____  \ |  `--'  |     |  |     |  | |  `----.|  `--'  | .----)   |      #
#        |__| \__| /__/     \__\ \______/      |__|     |__| |_______| \______/  |_______/       #
#                                                                                                #
#                                                                                                #
#                                                                                                #
#                                                                                                #
#                                  # #  ( )                                                      #
#                                   ___#_#___|__                                                 #
#                               _  |____________|  _                                             #
#                        _=====| | |            | | |==== _                                      #
#                  =====| |.---------------------------. | |====                                 #
#    <--------------------'   .  .  .  .  .  .  .  .   '--------------/                          #
#      \                                                             /                           #
#       \_______________________________________________WWS_________/                            #
#   wwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwww                        #
# wwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwww                       #
#    wwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwww                         #
#                                                                                                #
#                                                                                                #
# ################################################################################################
# Warning! All Nautilus systems are monitored and audited. Logoff immediately if you are not authorized!


# REPEAT THESE STEPS FOR ALL APP SERVERS ENDS


# ssh in to the db server
ssh peter@stdb01

# confirm scp doesn't exist
scp

# install openssh-clients
sudo yum -y install openssh-clients

# confirm it is installed
scp

# exit the server
exit


# REPEAT THE STEPS FROM THE BEGINNING FOR THE DB SERVER
```
