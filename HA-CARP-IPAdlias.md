## HA, CARP IPs, IP Aliases

If you have setup finally setup your HA system it’s time to add redundant IP addresses.

For this you can reach the configuration via Firewall -> Virtual IPs

 

Let’s say you have a /28, 212.11.11.0/28.

FW1: 212.11.11.11
FW2: 212.11.11.12

Your CARP IP: 212.11.11.1

If you want to add more HA IPs, e.g. bind to HAProxy of do some NAT you just need additional CARP IPs but with new groups. So new CARP IP, 212.11.11.2

 

An IP Alias is just an alias for the local interface and won’t get synced to the other machine in case of a failover, so just IP Alias on non redundant setup.

 

You only have to setup the CARP IP on the master node. All settings will be synced to the slave node, also with an increased skew

![CARP](/pictures/opn_carp_ipalias.jpg)

