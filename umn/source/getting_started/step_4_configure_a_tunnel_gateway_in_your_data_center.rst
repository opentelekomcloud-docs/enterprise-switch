:original_name: esw_qs_0007.html

.. _esw_qs_0007:

Step 4: Configure a Tunnel Gateway in Your Data Center
======================================================

Scenarios
---------

This section describes how to configure the tunnel gateway on a VXLAN tunnel switch of an on-premises data center.

The following uses CE6850 and H3C S6520 series switches as examples. To check more configurations, see the product documentation of the corresponding switch.

-  :ref:`Procedure (CE6850 Switches) <esw_qs_0007__section655520347165>`
-  :ref:`Procedure (H3C S6520 Switches) <esw_qs_0007__section1530011118427>`

Notes and Constraints
---------------------

If you use an enterprise switch to connect your on-premises data center to the cloud, the switches of your data center must support the VXLAN function. If high reliability is required, the VXLAN switches need to be deployed in disaster recovery mode.

The following lists some switch models that support the VXLAN function.

-  Huawei switches: Huawei CE58, CE68, CE78, and CE88 series switches, such as CE6870, CE6875, CE6881, CE6863, and CE12800 switches
-  Switches of other vendors: Cisco Nexus 9300 and H3C S6520 series switches

Networking Example
------------------

In this example, the Layer 2 subnet gateway and the VXLAN tunnel are on different switches.

The tunnel IP address on the cloud is 10.0.6.3, the tunnel IP address of the tunnel switch on the on-premises data center is 2.2.2.2, and the tunnel VNI is 5010.


.. figure:: /_static/images/en-us_image_0000001325432441.png
   :alt: **Figure 1** Layer 2 subnet gateway and VXLAN tunnel on different switches

   **Figure 1** Layer 2 subnet gateway and VXLAN tunnel on different switches

.. _esw_qs_0007__section655520347165:

Procedure (CE6850 Switches)
---------------------------

Configure the tunnel switch of your data center to divert the traffic of the VLAN corresponding to the Layer 2 subnet to the tunnel.

.. important::

   Currently, most CE series switches do not support forwarding of encapsulated VXLAN packets through Layer 3 sub-interfaces. Layer 3 sub-interfaces cannot be used by VXLAN uplinks (connected to enterprise switches). Instead, VLAN interfaces can be used.

#. Log in to the tunnel switch and run the **system-view** command to switch to the system view.

#. Switch to the loopback 0 interface view and configure the tunnel IP address.

   Example:

   **interface loopback 0**

   **ip address 2.2.2.2 255.255.255.255**

3. Use the **quit** command to exit the interface view and return to the system view.

4. Switch to the bridge domain (BD) view and configure the VXLAN VNI for the BD.

   Example:

   **bridge-domain 10**

   **vxlan vni 5010**

5. Use the **quit** command to exit the BD view and return to the system view.

6. Create a Layer 2 sub-interface and use the sub-interface to divert traffic from the VLAN at Layer 2 to the tunnel.

   Example:

   **interface 10ge 1/0/2.1 mode l2**

   **encapsulation dot1q vid 100**

   **bridge-domain 10**

7. Use the **interface nve** command to create an NVE interface, switch to the NVE interface view, and configure the IP address (2.2.2.2) for the source VTEP of the VXLAN tunnel.

   Example:

   **interface nve1**

   **source 2.2.2.2**

8. Use the **vni** command in the NVE interface view to configure an ingress replication list for VNI 5010.

   Example:

   **vni 5010 head-end peer-list 10.0.6.3**

9. Check the VXLAN configuration status in the system view:

   **display vxlan vni 5010 verbose**


   .. figure:: /_static/images/en-us_image_0000001275071870.png
      :alt: **Figure 2** VXLAN configuration status

      **Figure 2** VXLAN configuration status

   If the value of **State** is **up**, the tunnel status is normal.

.. _esw_qs_0007__section1530011118427:

Procedure (H3C S6520 Switches)
------------------------------

Establish a VXLAN tunnel between a VXLAN switch and an enterprise switch, associate the VXLAN tunnel with a VXLAN, so that Layer 2 packets from VMs can be encapsulated into IP packets and then sent to the enterprise switch. Configure Ethernet service instances and matching rules on downlink interfaces of a VXLAN switch to identify the VXLAN that packets belong to.

#. Configure the switch to work in VXLAN mode.

   Save the configuration, and restart the switch. (Skip this step if the switch is already working in VXLAN mode.)

   Example:

   <SwitchA> **system-view**

   [SwitchA] **switch-mode 1**

   .. code-block::

      Reboot device to make the configuration take effect.

   [SwitchA] **quit**

   <SwitchA> **reboot**

   .. code-block::

      Start to check configuration with next startup configuration file, please wait..
      .......DONE!
      Current configuration may be lost after the reboot, save current configuration?
      [Y/N]:y
      This command will reboot the device. Continue? [Y/N]:y

2. Create a tunnel interface and configure an IP address for the interface.

   Create a loopback interface and configure an IP address for the loopback interface as the remote IP address of the VXLAN tunnel.

   Example:

   [SwitchA] **interface loopback 0**

   [SwitchA-LoopBack0] **ip address 2.2.2.2 32**

   .. important::

      For a new interface IP address (including the loopback interface IP address) of the VXLAN switch, check whether there is a route to direct traffic from the IP address to the tunnel subnet of the enterprise switch. If there is no such a route, configure one on the VXLAN switch. The VXLAN switch can be an aggregation switch or a core switch. Select a switch based on the network plan.

3. Create a VXLAN.

   a. Enable L2VPN.

      Example:

      <SwitchA> **system-view**

      [SwitchA] **l2vpn enable**

   b. Enable Layer 2 forwarding for the VXLAN tunnel.

      Example:

      [SwitchA] **undo vxlan ip-forwarding**

   c. Create the VSI **vpna** and VXLAN 5010.

      Example:

      [SwitchA] **vsi vpna**

      [SwitchA-vsi-vpna] **vxlan 5010**

      [SwitchA-vsi-vpna-vxlan5010] **quit**

      [SwitchA-vsi-vpna] **quit**

      .. important::

         The VXLAN ID must be the same as the tunnel VNI in remote access information configured during Layer 2 connection creation in :ref:`Table 1 <esw_qs_0006__esw_ug_0007_en-us_topic_0228866532_table37675406>`.

4. Create a VXLAN tunnel.

   Create a VXLAN tunnel (Tunnel1) to the enterprise switch.

   Example:

   [SwitchA] **interface tunnel 1 mode vxlan**

   [SwitchA-Tunnel1] **source 2.2.2.2**

   [SwitchA-Tunnel1] **destination 10.0.6.3**

   [SwitchA-Tunnel1] **quit**

5. Associate the VXLAN with the VXLAN tunnel.

   On the VXLAN switch, associate the VXLAN tunnel (Tunnel1) with VXLAN 5010.

   Example:

   [SwitchA] **vsi vpna**

   [SwitchA-vsi-vpna] **vxlan 5010**

   [SwitchA-vsi-vpna-vxlan5010] **tunnel 1**

   [SwitchA-vsi-vpna-vxlan5010] **quit**

   [SwitchA-vsi-vpna] **quit**

   .. important::

      -  A maximum of six Layer 2 connections can be created on an enterprise switch. Each connection corresponds to a VXLAN. Multiple VXLANs can be associated with the same VXLAN tunnel, such as, Tunnel1.
      -  A VXLAN switch can connect to multiple enterprise switches. In this case, you can associate multiple VXLAN tunnels, for example, Tunnel1 and Tunnel2, with the same VXLAN.

6. Configure an Ethernet service instance to match frames and associate the instance with the VSI.

   Create Ethernet service instance 1000 on Bridge-Aggregation1 of the VXLAN switch to match frames of VLAN 100 and associate the instance with VSI **vpna** (VXLAN 5010).

   Example:

   [SwitchA] **Bridge-Aggregation 1**

   [SwitchA-Bridge-Aggregation1] **port link-type trunk**

   [SwitchA-Bridge-Aggregation1] **service-instance 1000**

   [SwitchA-Bridge-Aggregation1-srv1000] **encapsulation s-vid 100**

   [SwitchA-Bridge-Aggregation1-srv1000] **xconnect vsi vpna**

   [SwitchA-Bridge-Aggregation1-srv1000] **quit**

   [SwitchA-Bridge-Aggregation1] **quit**

   .. important::

      The method for creating Ethernet service instances on physical Ethernet interfaces of switches is similar.

7. Check the status of the VXLAN tunnel interface.

   -  The status of the VXLAN tunnel interface is **Up**.

      Example:

      [SwitchA]\ **display interface Tunnel 1**

      .. code-block::

         Tunnel1
         Current state: UP
         Line protocol state: UP
         Description: Tunnel1 Interface
         Bandwidth: 64 kbps
         Maximum transmission unit: 1464
         Internet protocol processing: Disabled
         Last clearing of counters: 17:19:44 Fri 01/18/2013
         Tunnel source 2.2.2.2, destination 10.0.6.3
         Tunnel protocol/transport UDP_VXLAN/IP
         Last 300 seconds input rate: 0 bytes/sec, 0 bits/sec, 0 packets/sec
         Last 300 seconds output rate: 0 bytes/sec, 0 bits/sec, 0 packets/sec
         Input: 0 packets, 0 bytes, 4 drops
         Output: 0 packets, 0 bytes, 0 drops

   -  Check the VSI information. The VXLAN tunnel associated with the VXLAN and the Ethernet service instance associated with the VSI are in **Up** status.

      Example:

      [SwitchA]\ **display l2vpn vsi verbose**

      .. code-block::

         VSI Name: vnpa
         VSI Index               : 1
         VSI State               : Up
         MTU                     : 1500
         Bandwidth               : -
         Broadcast Restrain      : -
         Multicast Restrain      : -
         Unknown Unicast Restrain: -
         MAC Learning            : Enabled
         MAC Table Limit         : -
         MAC Learning rate       : -
         Drop Unknown            : -
         Flooding                : Enabled
         Statistics              : Disabled
         VXLAN ID                : 5010
         Tunnels:
         Tunnel Name          Link ID    State    Type        Flood proxy
         Tunnel1              0x5000001  UP       Manual      Disabled
         ACs:
         AC                   Link ID    State    Type
         BAGG1 srv1000        0          Up       Manual
