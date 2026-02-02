:original_name: esw_qs_0004.html

.. _esw_qs_0004:

Step 1: Use Direct Connect or VPN to Communicate at Layer 3
===========================================================

Scenarios
---------

An enterprise switch establishes a Layer 2 network based on a Layer 3 network between an on-premises data center and a VPC. This section describes how to create a Direct Connect or VPN connection between an on-premises data center and a VPC at Layer 3.

Prerequisites
-------------

Before using enterprise switches, plan resources on and off the cloud by referring to :ref:`How Enterprise Switches Work <esw_pd_0003>`.

Procedure
---------

#. Create a Direct Connect or VPN connection.

   Select the VPC (vpc-01) where the enterprise switch is created in :ref:`Step 2: Create an Enterprise Switch <esw_qs_0005>`.

   For details, see `Configuring a Direct Connect Connection <https://docs.otc.t-systems.com/direct-connect/umn/getting_started/enabling_direct_connect/index.html#dc-02-0200>`__ or `Configuring a VPN Connection <https://docs.otc.t-systems.com/virtual-private-network/umn/getting_started/index.html>`__.

#. Submit a service ticket to check whether your Direct Connect or VPN connection supports VXLAN interconnection with an enterprise switch. If your connection does not support this, contact technical support.
