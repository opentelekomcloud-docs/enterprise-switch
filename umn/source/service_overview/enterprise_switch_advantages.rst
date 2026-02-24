:original_name: esw_pd_0004.html

.. _esw_pd_0004:

Enterprise Switch Advantages
============================

Generally, you may use **VPN or Direct Connect** to enable communications between on-premises data centers and VPCs at Layer 3. However, this may require network reconstruction, delay cloud migration, and cause service interruptions. For details, see :ref:`Constraints on Layer 3 Networking Between an On-Premises Data Center and the Cloud (Without Enterprise Switches) <esw_pd_0004__section11172133819576>`.

**Enterprise switches** allow communications between on-premises data centers and VPCs at Layer 2, helping you dynamically and smoothly migrate workloads to the cloud. For details, see :ref:`Advantages of Layer 2 Networking Between an On-Premises Data Center and the Cloud (Using an Enterprise Switch) <esw_pd_0004__section102921112145814>`.

.. _esw_pd_0004__section11172133819576:

Constraints on Layer 3 Networking Between an On-Premises Data Center and the Cloud (Without Enterprise Switches)
----------------------------------------------------------------------------------------------------------------

:ref:`Figure 1 <esw_pd_0004__fig36161843104515>` shows the Layer 3 networking between on-premises data centers and VPCs using VPN or Direct Connect. :ref:`Table 1 <esw_pd_0004__table127411948151510>` describes the pain points.

.. _esw_pd_0004__fig36161843104515:

.. figure:: /_static/images/en-us_image_0000001355941949.png
   :alt: **Figure 1** Layer 3 networking

   **Figure 1** Layer 3 networking

.. _esw_pd_0004__table127411948151510:

.. table:: **Table 1** Layer 3 networking description

   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Description                       | VPN or Direct Connect allows the communication between on-premises data centers and VPCs at Layer 3 through routes.                                                                                                                                                                                                                                                              |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Pain Points                       | -  The CIDR blocks of the on-premises data center and the VPC that are used for communication cannot overlap.                                                                                                                                                                                                                                                                    |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                  |
   |                                   |    On-premises workloads communicate with each other using IP addresses instead of domain names. If the CIDR blocks of the on-premises data center and the VPC that are used for communication overlap, the on-premises network needs to be reconstructed before the cloud migration, which prolongs the cloud migration period, interrupts businesses, and increases O&M costs. |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                  |
   |                                   | -  Workloads in a subnet have to be migrated together, and cloud and on-premises workloads in the same subnet cannot communicate with each other.                                                                                                                                                                                                                                |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                  |
   |                                   |    Dozens of different workloads are deployed on each subnet of the on-premises data center. If workloads are migrated by subnet, business continuity cannot be ensured.                                                                                                                                                                                                         |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _esw_pd_0004__section102921112145814:

Advantages of Layer 2 Networking Between an On-Premises Data Center and the Cloud (Using an Enterprise Switch)
--------------------------------------------------------------------------------------------------------------

To handle the pain points of cloud migration at Layer 3, you can use enterprise switches to allow the communication between on-premises data centers and VPCs at Layer 2. For details about the advantages of enterprise switches, see :ref:`Table 2 <esw_pd_0004__table1674110377231>`.


.. figure:: /_static/images/en-us_image_0000002424302708.png
   :alt: **Figure 2** Layer 2 networking diagram

   **Figure 2** Layer 2 networking diagram

.. _esw_pd_0004__table1674110377231:

.. table:: **Table 2** Layer 2 networking description

   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Description                       | Enterprise switches establish a Layer 2 network between on-premises data centers and VPCs based on the Layer 3 network established by VPN or Direct Connect.    |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Advantages                        | -  The CIDR blocks of the on-premises data center and the VPC that are used for communication can overlap.                                                      |
   |                                   |                                                                                                                                                                 |
   |                                   |    An enterprise switch allows the network of the on-premises data center to remain unchanged even if the data center and the VPC have overlapping CIDR blocks. |
   |                                   |                                                                                                                                                                 |
   |                                   | -  Workloads can be migrated to the cloud on a server basis, and cloud and on-premises workloads in the same subnet can communicate with each other.            |
   |                                   |                                                                                                                                                                 |
   |                                   |    Workloads can be seamlessly migrated to the cloud to prevent any loss caused by cloud migration.                                                             |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
