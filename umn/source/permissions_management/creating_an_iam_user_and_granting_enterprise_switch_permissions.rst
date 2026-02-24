:original_name: esw_ug_0012.html

.. _esw_ug_0012:

Creating an IAM User and Granting Enterprise Switch Permissions
===============================================================

This section describes how to use IAM to implement fine-grained permissions control for your enterprise switch resources. With IAM, you can:

-  Create IAM users for employees based on the organizational structure of your enterprise. Each IAM user has their own security credentials, providing access to enterprise switch resources.
-  Grant only the permissions required for users to perform a specific task.

If your account does not require individual IAM users, skip over this section.

:ref:`Figure 1 <esw_ug_0012__fig1351611812271>` shows the procedure for granting permissions.

Prerequisites
-------------

You have learned about the permissions supported by Enterprise Switch and choose policies or roles according to your requirements. Enterprise Switch uses the same system permissions as VPC. For details, see :ref:`Permissions <esw_pd_0007>`.

Process Flow
------------

.. _esw_ug_0012__fig1351611812271:

.. figure:: /_static/images/en-us_image_0000001217250348.png
   :alt: **Figure 1** Process for granting Enterprise Switch permissions

   **Figure 1** Process for granting Enterprise Switch permissions

#. .. _esw_ug_0012__li10176121316284:

   Create a user group and assign permissions.

   Create a user group on the IAM console, and assign the **Tenant Guest** policy to the group.

#. Create a user and add the user to the user group.

   Create a user on the IAM console and add the user to the group created in :ref:`1 <esw_ug_0012__li10176121316284>`.

#. Log in and verify permissions.

   Click **Service List** and choose **Enterprise Switch**. Then click **Create** in the upper right corner. If the enterprise switch fails to be created, the **Tenant Guest** permission has taken effect.
