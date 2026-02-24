:original_name: esw_qs_0003.html

.. _esw_qs_0003:

Quick Start
===========

Enterprise switches establish a Layer 2 network between on-premises data centers and VPCs based on the Layer 3 network established by VPN or Direct Connect. :ref:`Figure 1 <esw_qs_0003__fig11967172194610>` shows the configuration process of enterprise switches.

.. _esw_qs_0003__fig11967172194610:

.. figure:: /_static/images/en-us_image_0000001355402245.png
   :alt: **Figure 1** Enterprise switch configuration flowchart

   **Figure 1** Enterprise switch configuration flowchart

.. table:: **Table 1** Process description

   +-----+----------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | No. | Step                                                                             | Description                                                                                                                                                                                                                                                  |
   +=====+==================================================================================+==============================================================================================================================================================================================================================================================+
   | 1   | :ref:`Step 1: Use Direct Connect or VPN to Communicate at Layer 3 <esw_qs_0004>` | An enterprise switch establishes a Layer 2 network based on a Layer 3 network between an on-premises data center and a VPC. This section describes how to create a Direct Connect or VPN connection between an on-premises data center and a VPC at Layer 3. |
   +-----+----------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 2   | :ref:`Step 2: Create an Enterprise Switch <esw_qs_0005>`                         | This section describes how to create an enterprise switch. An enterprise switch allows Layer 2 communication between an on-premises data center and a VPC based on VPN or Direct Connect.                                                                    |
   +-----+----------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 3   | :ref:`Step 3: Create a Layer 2 Connection <esw_qs_0006>`                         | After an enterprise switch is created, you need to create a Layer 2 connection to enable the local Layer 2 connection subnet and the remote VXLAN switch to communicate at Layer 2.                                                                          |
   +-----+----------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 4   | :ref:`Step 4: Configure a Tunnel Gateway in Your Data Center <esw_qs_0007>`      | This section describes how to configure the tunnel gateway on a VXLAN tunnel switch of an on-premises data center.                                                                                                                                           |
   +-----+----------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
