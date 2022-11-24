# TASK

The backup server in the Stratos DC contains several template XML files used by the Nautilus application. However, these template XML files must be populated with valid data before they can be used. One of the daily tasks of a system admin working in the xFusionCorp industries is to apply string and file manipulation commands!

Replace all occurances of the string String to Submarine on the XML file /root/nautilus.xml located in the backup server.

# SOLUTION

```bash
# ssh into the backup server
shh clint@stbkp01

# view the content of the file
sudo cat /root/nautilus.xml

# replace string using sed command
sudo sed -i 's/String/Submarine/g' /root/nautilus.xml

# confirm replacement
sudo cat /root/nautilus.xml | grep 'String'
sudo cat /root/nautilus.xml | grep 'Submarine'
```
