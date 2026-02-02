:original_name: esw_pd_0006.html

.. _esw_pd_0006:

Notes and Constraints
=====================

Quota Limits
------------

.. table:: **Table 1** Quota limits

   +--------------------------------------------------------------------------------------+---------------+-------------------------------------------------+
   | Resource                                                                             | Default Quota | Where to Increase Quota                         |
   +======================================================================================+===============+=================================================+
   | Maximum number of enterprise switches per account                                    | 5             | Contact customer service to increase the quota. |
   +--------------------------------------------------------------------------------------+---------------+-------------------------------------------------+
   | Maximum number of VPCs that can be associated with an enterprise switch              | 1             | Increasing the quota is not allowed.            |
   +--------------------------------------------------------------------------------------+---------------+-------------------------------------------------+
   | Maximum number of Layer 2 connections supported by each subnet                       | 1             | Increasing the quota is not allowed.            |
   +--------------------------------------------------------------------------------------+---------------+-------------------------------------------------+
   | Maximum number of Layer 2 connections supported by each **small** enterprise switch  | 1             | Increasing the quota is not allowed.            |
   +--------------------------------------------------------------------------------------+---------------+-------------------------------------------------+
   | Maximum number of Layer 2 connections supported by each **medium** enterprise switch | 3             | Increasing the quota is not allowed.            |
   +--------------------------------------------------------------------------------------+---------------+-------------------------------------------------+
   | Maximum number of Layer 2 connections supported by each **large** enterprise switch  | 6             | Increasing the quota is not allowed.            |
   +--------------------------------------------------------------------------------------+---------------+-------------------------------------------------+

Constraints
-----------

-  Enterprise switches cannot forward untrusted unicast, broadcast, and multicast (except VRRP) packets from your data center to the cloud or IPv6 packets.

-  On-premises servers cannot use advanced network functions on the cloud, such as VPC Peering, Route Table, ELB, and NAT Gateway.

-  If you want to use a Direct Connect connection together with an enterprise switch, submit a service ticket to check whether your connection can interconnect with an enterprise switch. If your connection does not support this, contact technical support.

-  If you want to use a VPN connection together with an enterprise switch, submit a service ticket to check whether your connection supports VXLAN interconnection with an enterprise switch. If your connection does not support this, contact technical support.

-  If cloud and on-premises networks communicate with each other at Layer 2, the cloud subnet gateway address must be the same as the on-premises subnet gateway address. Otherwise, the on-premises subnet gateway address may conflict with the IP address of a cloud server, causing communication exceptions.

-  Each enterprise switch allows up to 10,000 IP addresses to communicate at Layer 2, including a maximum of 1,000 on-premises IP addresses.

-  To use an enterprise switch to connect cloud and on-premises networks at Layer 2, you are responsible for constructing the VXLAN network in your data center, such as preparing VXLAN switches, connecting physical networks, and connecting to Direct Connect or VPN.

-  Generally, a server determines the destination MAC address of a reply packet through ARP. However, some hosts or hardware devices (such as F5 load balancers) are configured to use the source MAC address of a request packet as the destination MAC address of its reply packet. If an enterprise switch is used for cloud and on-premises communications at Layer 3, a network disconnection may occur.

   For example, an enterprise switch allows cloud and on-premises networks to communicate on 192.168.3.0/24. If the cloud server using an IP address in 192.168.2.2/24 accesses the on-premises server using an IP address in 192.168.3.3/24, the request packet on the cloud is sent to the on-premises server through the VPC route and then the enterprise switch. The reply packet from the on-premises server is sent back to the cloud through the route and Direct Connect or VPN. If the on-premises server is configured to use the source MAC address of a request packet as the destination MAC address of its reply packet, the destination MAC address of the reply packet is not the MAC address of gateway 192.168.3.0/24, but the source MAC address of the request packet, that is, the MAC address of the enterprise switch. In this case, the destination MAC address of the reply packet is incorrect and the network is disconnected.

-  If an enterprise switch uses the VXLAN protocol, the VXLAN protocol has a header of 50 bytes and the packet length increases. Your on-premises network devices that allow VXLAN packets should support jumbo frames (Ethernet frames whose MTU is greater than 1500 bytes). Otherwise, such packets cannot be transmitted.

-  If you use an enterprise switch to connect your on-premises data center to the cloud, the switches of your data center must support the VXLAN function. The following lists some switches that support the VXLAN function.

   -  Huawei switches: Huawei CE58, CE68, CE78, and CE88 series switches, such as CE6870, CE6875, CE6881, CE6863, and CE12800 switches
   -  Switches of other vendors: Cisco Nexus 9300 and H3C S6520 series switches
