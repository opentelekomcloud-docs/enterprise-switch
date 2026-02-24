:original_name: esw_pd_0003.html

.. _esw_pd_0003:

How Enterprise Switches Work
============================

:ref:`Figure 1 <esw_pd_0003__fig1669183443911>` illustrates how an enterprise switch works. :ref:`Table 1 <esw_pd_0003__table92245524493>` describes the working principles in more detail.

.. _esw_pd_0003__fig1669183443911:

.. figure:: /_static/images/en-us_image_0000001303019660.png
   :alt: **Figure 1** Networking

   **Figure 1** Networking

.. _esw_pd_0003__table92245524493:

.. table:: **Table 1** Working principles

   +-----------------------+-----------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | No.                   | Action                                                                                                          | Description                                                                                                                                                |
   +=======================+=================================================================================================================+============================================================================================================================================================+
   | 1                     | Enable the local and remote :ref:`tunnel subnets <esw_pd_0003__section153446227585>` to communicate at Layer 3. | -  Plan resources on and off the cloud. For details, see :ref:`Table 2 <esw_pd_0003__table23411392566>`.                                                   |
   |                       |                                                                                                                 | -  Use Direct Connect or VPN to enable the local (Subnet-tunnel-L01) and remote (Subnet-tunnel-R01) tunnel subnets to communicate at Layer 3.              |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 2                     | Create an enterprise switch and specify a :ref:`tunnel subnet <esw_pd_0003__section153446227585>`.              | Create an enterprise switch, set the local tunnel subnet to **Subnet-tunnel-L01**, and the local tunnel IP address to **192.168.100.101**.                 |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 3                     | Create a :ref:`Layer 2 connection <esw_pd_0003__section173118361915>`.                                          | Create a Layer 2 connection to enable the local Layer 2 connection subnet (Subnet-layer-L01) and the remote VXLAN switch to communicate at Layer 2.        |
   |                       |                                                                                                                 |                                                                                                                                                            |
   |                       |                                                                                                                 | Configure the following parameters:                                                                                                                        |
   |                       |                                                                                                                 |                                                                                                                                                            |
   |                       |                                                                                                                 | -  :ref:`Active and standby interface IP addresses <esw_pd_0003__section611318438393>`: They can be automatically assigned or manually specified.          |
   |                       |                                                                                                                 | -  :ref:`Remote tunnel IP address <esw_pd_0003__section14650913105915>` (200.51.51.100) and :ref:`tunnel VNI <esw_pd_0003__section12852123520284>` (10001) |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 4                     | Configure a tunnel gateway in the on-premises data center.                                                      | Configure a tunnel gateway on the remote VXLAN switch to establish a VXLAN tunnel for the remote Layer 2 connection subnet (Subnet-layer-R01).             |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _esw_pd_0003__table23411392566:

.. table:: **Table 2** Resource details

   +-----------------------------------------------------------------------+-------------------------------------------------------------------------------------+----------------------------------------------+---------------------------------------------------------------+-----------------------------------+
   | Resource                                                              | Cloud (Local)                                                                       |                                              | On Premises (Remote)                                          |                                   |
   +=======================================================================+=====================================================================================+==============================================+===============================================================+===================================+
   | :ref:`Layer 2 connection subnet <esw_pd_0003__section48931413175817>` | VPC subnet                                                                          | Subnet-layer-L01: 192.168.0.0/24             | On-premises subnet                                            | Subnet-layer-R01: 192.168.0.0/24  |
   +-----------------------------------------------------------------------+-------------------------------------------------------------------------------------+----------------------------------------------+---------------------------------------------------------------+-----------------------------------+
   |                                                                       | ECS                                                                                 | -  ECS-layer-L01-A: 192.168.0.50             | On-premises server                                            | -  VM-layer-R01-A: 192.168.0.60   |
   |                                                                       |                                                                                     | -  ECS-layer-L01-B: 192.168.0.51             |                                                               | -  VM-layer-R01-B: 192.168.0.61   |
   +-----------------------------------------------------------------------+-------------------------------------------------------------------------------------+----------------------------------------------+---------------------------------------------------------------+-----------------------------------+
   |                                                                       | :ref:`Active and standby interface IP addresses <esw_pd_0003__section611318438393>` | -  Active interface IP address: 192.168.0.7  | ``-``                                                         | ``-``                             |
   |                                                                       |                                                                                     | -  Standby interface IP address: 192.168.0.8 |                                                               |                                   |
   +-----------------------------------------------------------------------+-------------------------------------------------------------------------------------+----------------------------------------------+---------------------------------------------------------------+-----------------------------------+
   | :ref:`Tunnel subnet <esw_pd_0003__section153446227585>`               | VPC subnet                                                                          | Subnet-tunnel-L01: 192.168.100.0/24          | On-premises subnet                                            | Subnet-tunnel-R01: 200.51.51.0/24 |
   +-----------------------------------------------------------------------+-------------------------------------------------------------------------------------+----------------------------------------------+---------------------------------------------------------------+-----------------------------------+
   |                                                                       | :ref:`Tunnel IP address <esw_pd_0003__section14650913105915>`                       | 192.168.100.101                              | :ref:`Tunnel IP address <esw_pd_0003__section14650913105915>` | 200.51.51.100                     |
   +-----------------------------------------------------------------------+-------------------------------------------------------------------------------------+----------------------------------------------+---------------------------------------------------------------+-----------------------------------+
   | :ref:`Tunnel VNI <esw_pd_0003__section12852123520284>`                | 10001                                                                               |                                              |                                                               |                                   |
   +-----------------------------------------------------------------------+-------------------------------------------------------------------------------------+----------------------------------------------+---------------------------------------------------------------+-----------------------------------+

.. _esw_pd_0003__section48931413175817:

Layer 2 Connection Subnets
--------------------------

Layer 2 connection subnets include a local Layer 2 connection subnet and a remote Layer 2 connection subnet. They are used for communications at Layer 2.

-  Local Layer 2 connection subnet: a VPC subnet, for example, Subnet-layer-L01
-  Remote Layer 2 connection subnet: an on-premises subnet, for example, Subnet-layer-R01

Constraints

-  The local and remote Layer 2 connection subnets can overlap, but the IP addresses of the servers that need to communicate in the local and remote subnets must be different. Otherwise, the communication fails.
-  A VPC subnet that has been used by a Layer 2 connection cannot be used by any other Layer 2 connections or enterprise switches.

.. _esw_pd_0003__section153446227585:

Tunnel Subnets
--------------

Local and remote tunnel subnets communicate with each other at Layer 3 over Direct Connect or VPN. Enterprise switches allow communications between cloud and on-premises networks at Layer 2 based on the Layer 3 network between tunnel subnets.

-  Local tunnel subnet: a VPC subnet, for example, Subnet-tunnel-L01
-  Remote tunnel subnet: an on-premises subnet, for example, Subnet-tunnel-R01

Constraints

-  Ensure that the local and remote tunnel subnets can communicate at Layer 3 over VPN or Direct Connect before you use an enterprise switch to allow communication at Layer 2.
-  The switch in an on-premises data center must support VXLAN because the enterprise switch needs to establish a VXLAN tunnel to the data center at Layer 2.
-  The local tunnel subnet must have three IP addresses reserved for the enterprise switch.

.. _esw_pd_0003__section173118361915:

Layer 2 Connections
-------------------

After an enterprise switch is created, you need to create a Layer 2 connection to enable the local Layer 2 connection subnet and the remote VXLAN switch to communicate with each other at Layer 2.

Constraints

-  Each Layer 2 connection connects a local and a remote Layer 2 connection subnet. Each enterprise switch supports a maximum of six Layer 2 connections.
-  The Layer 2 connections of an enterprise switch can share a tunnel IP address, but their tunnel VNIs must be unique. A tunnel VNI is the identifier of a tunnel.
-  If a Layer 2 connection connects a local Layer 2 connection subnet to an enterprise switch, the local Layer 2 connection subnet must have two IP addresses reserved as active and standby interface IP addresses. The two IP addresses cannot be used by any local resources and must be different from the IP addresses in the remote Layer 2 connection subnet.

.. _esw_pd_0003__section611318438393:

Active and Standby Interface IP Addresses
-----------------------------------------

If a Layer 2 connection connects a local Layer 2 connection subnet to an enterprise switch, the local Layer 2 connection subnet must have two IP addresses reserved as active and standby interface IP addresses.

.. _esw_pd_0003__section14650913105915:

Tunnel IP Addresses
-------------------

If an enterprise switch establishes a VXLAN tunnel with an on-premises data center at Layer 2, each end of the VXLAN tunnel requires a tunnel IP address (the local and remote tunnel IP addresses). The two IP addresses must be different.

-  Local tunnel IP address: in the local tunnel subnet. In this example, the local tunnel subnet is Subnet-tunnel-L01, and the tunnel IP address is 192.168.100.101.
-  Remote tunnel IP address: in the remote tunnel subnet. In this example, the remote tunnel subnet is Subnet-tunnel-R01, and the tunnel IP address is 200.51.51.100.

.. _esw_pd_0003__section12852123520284:

Tunnel VNIs
-----------

Tunnel VNIs are used to uniquely identify the VXLAN tunnels between an on-premises data center and an enterprise switch.

For the same VXLAN tunnel, the on-premises data center and the cloud must use the same tunnel VNI.
