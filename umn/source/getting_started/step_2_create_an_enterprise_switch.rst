:original_name: esw_qs_0005.html

.. _esw_qs_0005:

Step 2: Create an Enterprise Switch
===================================

Scenarios
---------

This section describes how to create an enterprise switch. An enterprise switch allows Layer 2 communication between an on-premises data center and a VPC based on VPN or Direct Connect.

Prerequisites
-------------

-  You have planned the resources required both on the cloud and on premises. For details about resource planning, see :ref:`How Enterprise Switches Work <esw_pd_0003>`.
-  An enterprise switch establishes a Layer 2 network based on a Layer 3 network between an on-premises data center and a VPC created by VPN. You need to create a Direct Connect or VPN connection first by referring to :ref:`Step 1: Use Direct Connect or VPN to Communicate at Layer 3 <esw_qs_0004>`.

Constraints
-----------

-  The switch in an on-premises data center must support VXLAN because the enterprise switch needs to establish a VXLAN tunnel to the data center at Layer 2.
-  The local tunnel subnet must have three IP addresses reserved for the enterprise switch.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. On the console homepage, choose **Network** > **Enterprise Switch**.

   The **Enterprise Switch** page is displayed.

#. In the upper right corner of the page, click **Create**.

   The page for creating an enterprise switch is displayed.

#. Configure the parameters as prompted. For details, see :ref:`Table 1 <esw_qs_0005__esw_ug_0002_table19458111044410>`.


   .. figure:: /_static/images/en-us_image_0000002516958061.png
      :alt: **Figure 1** Purchasing an enterprise switch

      **Figure 1** Purchasing an enterprise switch

   .. _esw_qs_0005__esw_ug_0002_table19458111044410:

   .. table:: **Table 1** Parameters for creating an enterprise switch

      +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Parameter               | Description                                                                                                                                                                                                                                        | Example Value                   |
      +=========================+====================================================================================================================================================================================================================================================+=================================+
      | Region                  | Mandatory                                                                                                                                                                                                                                          | ``-``                           |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         | Select the region nearest to you to ensure the lowest latency possible.                                                                                                                                                                            |                                 |
      +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Active AZ               | Mandatory                                                                                                                                                                                                                                          | AZ1                             |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         | Select the AZ where the active node is deployed. Enterprise switches are deployed in active/standby mode.                                                                                                                                          |                                 |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         | An active AZ carries traffic. You can set the AZ to the one where your ECSs that need to communicate with an on-premises data center are deployed to ensure quick and uninterrupted access to ECSs.                                                |                                 |
      +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Standby AZ              | Mandatory                                                                                                                                                                                                                                          | AZ2                             |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         | Select the AZ where the standby node is deployed. Set the standby AZ to be different from the active AZ.                                                                                                                                           |                                 |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         | A standby AZ is used for backup and disaster recovery.                                                                                                                                                                                             |                                 |
      +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Specifications          | Mandatory                                                                                                                                                                                                                                          | Basic                           |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         | Currently, the following enterprise switch specifications are supported:                                                                                                                                                                           |                                 |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         | -  Basic                                                                                                                                                                                                                                           |                                 |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         |    -  Maximum Bandwidth: 3 Gbit/s                                                                                                                                                                                                                  |                                 |
      |                         |    -  Maximum PPS: 500,000                                                                                                                                                                                                                         |                                 |
      |                         |    -  Connected Subnets: 1                                                                                                                                                                                                                         |                                 |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         | -  Standard                                                                                                                                                                                                                                        |                                 |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         |    -  Maximum Bandwidth: 5 Gbit/s                                                                                                                                                                                                                  |                                 |
      |                         |    -  Maximum PPS: 1,000,000                                                                                                                                                                                                                       |                                 |
      |                         |    -  Connected Subnets: 3                                                                                                                                                                                                                         |                                 |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         | -  Enhanced                                                                                                                                                                                                                                        |                                 |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         |    -  Maximum Bandwidth: 10 Gbit/s                                                                                                                                                                                                                 |                                 |
      |                         |    -  Maximum PPS: 2,000,000                                                                                                                                                                                                                       |                                 |
      |                         |    -  Connected Subnets: 6                                                                                                                                                                                                                         |                                 |
      +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | VPC                     | Mandatory                                                                                                                                                                                                                                          | vpc-01                          |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         | VPC that the enterprise switch belongs to.                                                                                                                                                                                                         |                                 |
      +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Tunnel Subnet           | Mandatory                                                                                                                                                                                                                                          | subnet-01                       |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         | Subnet of the VPC that the enterprise switch belongs to. It is the local tunnel subnet.                                                                                                                                                            |                                 |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         | Local and remote tunnel subnets communicate with each other at Layer 3 over Direct Connect or VPN. Enterprise switches allow communications between cloud and on-premises networks at Layer 2 based on the Layer 3 network between tunnel subnets. |                                 |
      +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Local Tunnel IP Address | Mandatory                                                                                                                                                                                                                                          | Automatically assign IP address |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         | IP address in the local tunnel subnet, which can be automatically assigned or manually specified.                                                                                                                                                  |                                 |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         | If an enterprise switch establishes a VXLAN tunnel with an on-premises data center at Layer 2, each end of the VXLAN tunnel requires a tunnel IP address (the local and remote tunnel IP addresses). The two IP addresses must be different.       |                                 |
      +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Name                    | Mandatory                                                                                                                                                                                                                                          | esw-01                          |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         | Enter the name of the enterprise switch. The name:                                                                                                                                                                                                 |                                 |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         | -  Must contain 1 to 64 characters.                                                                                                                                                                                                                |                                 |
      |                         | -  Can contain letters, digits, underscores (_), hyphens (-), and periods (.).                                                                                                                                                                     |                                 |
      +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Description             | Optional                                                                                                                                                                                                                                           | ``-``                           |
      |                         |                                                                                                                                                                                                                                                    |                                 |
      |                         | Enter the description of the enterprise switch in the text box as required.                                                                                                                                                                        |                                 |
      +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+

#. Click **Next**.

#. On the displayed page, confirm the enterprise switch information and click **Submit**.

   This operation takes 3 to 6 minutes to complete. If the status is **Running**, the enterprise switch is created.

Follow-Up Operations
--------------------

After an enterprise switch is created, you need to create a Layer 2 connection and configure a remote tunnel gateway. For details, see :ref:`Getting Started <esw_qs_0003>`.

.. |image1| image:: /_static/images/en-us_image_0000002007168470.png
