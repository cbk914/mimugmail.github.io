## Easy and quick WIFI authentication against local FreeRADIUS

Attention: With this setup there's no check against certificates, don't use it in high production networks.
For home use it's just fine!

To authenticate your WIFI users against a local FreeRADIUS just install the plugin the usual way, drive to 

- Services
- FreeRADIUS
- General
 
enable FreeRADIUS and click Save.

Go further to "Client" and add a client with the IP address of your access point and a shared secret:

![client](/pictures/opn_freeradius_client1.jpg)

The go to "User" and add some users. "Username" and "Password" is perfectly enough:

![user](/pictures/opn_freeradius_user1.jpg)

Then surf to your access point, change authentication to WPA2-Enterprise, set the Radius Server (IP of your OPNsense), the shared secret and save.

Here's an example of a WAP121 Cisco SMB AP:

![WAP121](/pictures/opn_freeradius_wap121.jpg)

When you go to you clients just choose the network and you'll be prompted for User/PW. 
Here are examples of Linux and Android (it's important to choose PEAP / MD5 / no certificate validation):

Linux:
![Linux](/pictures/opn_freeradius_linux.jpg)


Android:
![Android](/pictures/opn_freeradius_android.jpg)


For Windows it just pops up for User/PW, type it in, say yes to the certificate warning and you're done!


That's all!
