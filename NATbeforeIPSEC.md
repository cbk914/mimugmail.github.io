## NAT before IPSEC

If you ever have to setup an IPSEC tunnel with an external party you know how fast things can go complicated. 
Most of the time it's the lack of knowledge about IPSEC as most administrators are just clicking the setup together.

When the tunnel is brought up and the years past by there could be a reason you need to access VPN endpoints via newly created networks (e.g. a new development department).

The easiest way to solve this is extending the VPN, but perhaps there are new administrators with fewer knowledge or there are some political reasons why VPN is not allowed to extended.
Here comes NAT into play!

Let's say your VPN secures your LAN 10.0.0.0/24 and the remote LAN 192.168.0.0/24. If your new development department in 10.0.1.0/24 needs to access the remote end you can easily NAT 10.0.1.0 to 10.0.0.0.
The packets match the SA and remote endpoints only see 10.0.0.0.

In order to complete this step open your Phase2 for the corresponding tunnel and add 10.0.1.0/24 to "Manual SPD entries".
This will create a new SPD redirecting packets from 10.0.1.0 to the tunnel. 

After this you have to create a One-to-one NAT hiding 10.0.1.0/24 to 10.0.0.0/24. 
With this setup the remote end only sees e.g. 10.0.0.166 when your client 10.0.1.166 connects via tunnel.

![NAT](/pictures/opn_ipsec_nat.jpg)

That's all!
