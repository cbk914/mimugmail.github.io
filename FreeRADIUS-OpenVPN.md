## OpenVPN authentication against local FreeRADIUS

To authenticate your OpenVPN instance against a local FreeRADIUS just install the plugin the usual way, drive to 

- Services
- FreeRADIUS
- General
 
enable FreeRADIUS and click Save.

Go further to "Client" and add a client "localhost" with IP address "127.0.0.1" and a shared secret:

![client](/pictures/opn_freeradius_client1.jpg)

The go to "User" and add some users. "Username" and "Password" is perfectly enough:

![user](/pictures/opn_freeradius_user1.jpg)

Now browse to 

- System
- Access
- Servers

and add a Radius server with IP address "127.0.0.1" and the shared secret you defined above.

After this go to 

- VPN
- OpenVPN
- Servers

and change the "Backend for authentication" to your defined radius instance.


That's all!
