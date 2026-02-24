:original_name: esw_qs_0008.html

.. _esw_qs_0008:

Step 5: Verify Network Connectivity
===================================

Scenarios
---------

Assume that there is an ECS (**ecs-demo-01**) running in the local subnet and an ECS (**ecs-demo-02**) running in the remote subnet with the IP address of 10.1.1.105. You can follow this section to log in to **ecs-demo-01** and verify the network connectivity between VPCs.

Procedure
---------

#. .. _esw_qs_0008__li154091419132410:

   Log in to the ECS.

#. .. _esw_qs_0008__li105742451915:

   Run the following command on the ECS:

   **ping** *<private-IP-address-of-the-ECS>*

   To verify the network connectivity between **vpc-01** and **vpc-02**, log in to **ecs-demo-01** and run the following command:

   **ping 10.1.1.105**

   If information similar to the following is displayed, the two VPCs can communicate with each other.

   |image1|

#. Repeat :ref:`1 <esw_qs_0008__li154091419132410>` to :ref:`2 <esw_qs_0008__li105742451915>` to verify the connectivity between other VPCs.

.. |image1| image:: /_static/images/en-us_image_0000002515685622.png
