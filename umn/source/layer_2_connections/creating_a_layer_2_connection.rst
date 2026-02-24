:original_name: esw_ug_0007.html

.. _esw_ug_0007:

Creating a Layer 2 Connection
=============================

Scenarios
---------

After an enterprise switch is created, you need to create a Layer 2 connection to enable the local Layer 2 connection subnet and the remote VXLAN switch to communicate at Layer 2.

Notes and Constraints
---------------------

-  Each Layer 2 connection connects a local and a remote Layer 2 connection subnet. Each enterprise switch supports a maximum of six Layer 2 connections.
-  The Layer 2 connections of an enterprise switch can share a tunnel IP address, but their tunnel VNIs must be unique. A tunnel VNI is the identifier of a tunnel.
-  If a Layer 2 connection connects a local Layer 2 connection subnet to an enterprise switch, the local Layer 2 connection subnet must have two IP addresses reserved as active and standby interface IP addresses. The two IP addresses cannot be used by any local resources and must be different from the IP addresses in the remote Layer 2 connection subnet.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. On the console homepage, choose **Network** > **Enterprise Switch**.

   The **Enterprise Switch** page is displayed.

4. Click the name of the target enterprise switch.

   The enterprise switch details page is displayed.

5. In the lower right part of the enterprise switch details page, click **Create Connection**.

   The page for creating a Layer 2 connection is displayed.


   .. figure:: /_static/images/en-us_image_0000002516237194.png
      :alt: **Figure 1** Creating a Layer 2 connection

      **Figure 1** Creating a Layer 2 connection

6. Configure the parameters as prompted. For details, see :ref:`Table 1 <esw_ug_0007__en-us_topic_0228866532_table37675406>`.

   .. _esw_ug_0007__en-us_topic_0228866532_table37675406:

   .. table:: **Table 1** Parameters for creating a Layer 2 connection

      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter                                     | Description                                                                                                                                                                                                                                                    | Example Value         |
      +===============================================+================================================================================================================================================================================================================================================================+=======================+
      | Enterprise Switch                             | Name of the enterprise switch. You do not need to set this parameter.                                                                                                                                                                                          | l2cg-01               |
      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | VPC                                           | VPC that is associated with the enterprise switch, which is the VPC that the local tunnel subnet belongs to. You do not need to set this parameter.                                                                                                            | vpc-01                |
      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Layer 2 Connection Subnet                     | Mandatory                                                                                                                                                                                                                                                      | subnet-02             |
      |                                               |                                                                                                                                                                                                                                                                |                       |
      |                                               | Select the layer 2 connection subnet in the VPC. This Layer 2 connection subnet is used to communicate with the Layer 2 connection subnet in an on-premises data center at Layer 2.                                                                            |                       |
      |                                               |                                                                                                                                                                                                                                                                |                       |
      |                                               | -  The local and remote Layer 2 connection subnets can overlap, but the IP addresses of the servers that need to communicate in the local and remote subnets must be different. Otherwise, the communication fails.                                            |                       |
      |                                               | -  A VPC subnet that has been used by a Layer 2 connection cannot be used by any other Layer 2 connections or enterprise switches.                                                                                                                             |                       |
      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Interface IP Address                          | Mandatory                                                                                                                                                                                                                                                      | Automatically assign  |
      |                                               |                                                                                                                                                                                                                                                                |                       |
      |                                               | IP addresses in the VPC subnet that are connected to the enterprise switch, including active and standby interface IP addresses. The IP addresses can be automatically assigned or manually specified.                                                         |                       |
      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Remote Access Information > Tunnel VNI        | Mandatory                                                                                                                                                                                                                                                      | 10001                 |
      |                                               |                                                                                                                                                                                                                                                                |                       |
      |                                               | Network identifier of the VXLAN tunnel used by an on-premises data center to connect to an enterprise switch, which is used to uniquely identify the VXLAN. For the same VXLAN tunnel, the on-premises data center and the cloud must use the same tunnel VNI. |                       |
      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Remote Access Information > Tunnel IP Address | Mandatory                                                                                                                                                                                                                                                      | 192.168.2.11          |
      |                                               |                                                                                                                                                                                                                                                                |                       |
      |                                               | IP address of the VXLAN tunnel used by the on-premises data center to connect to the enterprise switch.                                                                                                                                                        |                       |
      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Remote Access Information > Tunnel Port       | Port number of the VXLAN tunnel used by the on-premises data center to connect to the enterprise switch. Port **4789** is used by default. You do not need to set this parameter.                                                                              | 4789                  |
      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Name                                          | Mandatory                                                                                                                                                                                                                                                      | l2conn-01             |
      |                                               |                                                                                                                                                                                                                                                                |                       |
      |                                               | Enter the name of the Layer 2 connection. The name:                                                                                                                                                                                                            |                       |
      |                                               |                                                                                                                                                                                                                                                                |                       |
      |                                               | -  Must contain 1 to 64 characters.                                                                                                                                                                                                                            |                       |
      |                                               | -  Can contain letters, digits, underscores (_), hyphens (-), and periods (.).                                                                                                                                                                                 |                       |
      +-----------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

7. Click **Create**.

   This operation takes 20 to 60 seconds to complete. If the status is **Not connected** or **Connected**, the Layer 2 connection is created.

.. |image1| image:: /_static/images/en-us_image_0000002007168462.png
