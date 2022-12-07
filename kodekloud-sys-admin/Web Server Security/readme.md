# TASK

During a recent security audit, the application security team of xFusionCorp Industries found security issues with the Apache web server on Nautilus App Server 2 server in Stratos DC. They have listed several security issues that need to be fixed on this server. Please apply the security settings below:

a. On Nautilus App Server 2 it was identified that the Apache web server is exposing the version number. Ensure this server has the appropriate settings to hide the version number of the Apache web server.

b. There is a website hosted under `/var/www/html/blog` on `App Server 2`. It was detected that the directory `/blog` lists all of its contents while browsing the URL. Disable the directory browser listing in Apache config.

c. Also make sure to restart the Apache service after making the changes.

# SOLUTION

```bash
ssh steve@stapp02

systemctl status httpd

sudo vi /etc/httpd/conf/httpd.conf

# add the following line to the configuration file

# ServerTokens Prod
# ServerSignature Off

# <Directory /var/www/html/bog >
#         Options FollowSymLinks
#         AllowOverride None
#         Require all granted
# </Directory>

# search for `Options Indexes FollowSymLinks` and remove the `Indexes`

sudo systemctl start httpd

sudo systemctl restart httpd

systemctl status httpd.service
```
