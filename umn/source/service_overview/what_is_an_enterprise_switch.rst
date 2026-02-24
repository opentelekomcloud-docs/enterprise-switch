:original_name: esw_pd_0002.html

.. _esw_pd_0002:

What Is an Enterprise Switch?
=============================

Enterprise switches enable Layer 2 networking for VPCs, helping you to connect cloud and on-premises networks that are highly reliable, in a large scale, and of high performance.

Currently, enterprise switches only support Layer 2 connection gateways (L2CGs). An L2CG is a virtual tunnel gateway that can work with Direct Connect or VPN to establish network communications between cloud and on-premises networks at Layer 2. The gateway allows you to migrate workloads in data centers or private clouds to the cloud without changing subnets and IP addresses.

VPN or Direct Connect only allows cloud and on-premises networks to communicate with each other at Layer 3 and the CIDR blocks of the networks that are used for communication cannot overlap.

If the cloud and on-premises networks overlap and need to communicate with each other, you can use an enterprise switch to enable communication between them at Layer 2.

An enterprise switch is a tunnel gateway of a VPC and corresponds to the tunnel gateway of your data center. It can work together with Direct Connect or VPN to enable communications between a VPC and your on-premises data center at Layer 2. :ref:`Figure 1 <esw_pd_0002__fig7806391364>` shows the networking diagram. You need to connect a VPC subnet to the enterprise switch and specify the enterprise switch to establish a connection with the tunnel gateway of your on-premises data center so that the VPC subnet can communicate with the data center subnet at Layer 2.

.. _esw_pd_0002__fig7806391364:

.. figure:: /_static/images/en-us_image_0000001355818125.png
   :alt: **Figure 1** Layer 2 networking

   **Figure 1** Layer 2 networking
