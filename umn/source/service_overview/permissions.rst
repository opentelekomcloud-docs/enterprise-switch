:original_name: esw_pd_0007.html

.. _esw_pd_0007:

Permissions
===========

If you need to assign different permissions to employees in your enterprise to control their access to your enterprise switches, you can use Identity and Access Management (IAM) for fine-grained permissions management. IAM provides functions such as identity authentication, permissions management, and access control.

With IAM, you can create IAM users and assign permissions to the users to control their access to specific resources.

If your account does not need individual IAM users for permissions management, skip this section.

IAM can be used free of charge. You pay only for the resources in your account. For more information about IAM, see "Service Overview" in the *Identity and Access Management User Guide*.

Enterprise Switch Permissions
-----------------------------

By default, new IAM users do not have any permissions assigned. You need to add them to one or more groups and attach roles to these groups so that these users can inherit permissions from the groups and perform specified operations on cloud services.

Enterprise Switch is a project-level service deployed and accessed in specific physical regions. You need to select a project for which the permissions will be granted. If you select **All projects**, the permissions will be granted for all the projects. You need to switch to the authorized region before accessing Enterprise Switch.

Enterprise Switch uses the same system permissions as VPC. :ref:`Table 1 <esw_pd_0007__table72071540144910>` lists all the system-defined roles and policies supported by VPC. This VPC role is dependent on other roles. When assigning VPC roles to users, you need to also assign dependent roles for the VPC permissions to take effect.

.. _esw_pd_0007__table72071540144910:

.. table:: **Table 1** System-defined permissions for VPC

   +--------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
   | Policy Name        | Description                                                                                                             | Policy Type           | Dependencies                                                                                                                 |
   +====================+=========================================================================================================================+=======================+==============================================================================================================================+
   | VPC FullAccess     | Full permissions for VPC.                                                                                               | System-defined policy | To use the VPC flow log function, users must also have the **LTS ReadOnlyAccess** permission.                                |
   +--------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
   | VPC ReadOnlyAccess | Read-only permissions on VPC.                                                                                           | System-defined policy | None                                                                                                                         |
   +--------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
   | VPC Administrator  | Most permissions on VPC, excluding creating, modifying, deleting, and viewing security groups and security group rules. | System-defined role   | **Tenant Guest** and **Server Administrator** policies, which must be attached in the same project as **VPC Administrator**. |
   |                    |                                                                                                                         |                       |                                                                                                                              |
   |                    | To be granted this permission, users must also have the **Tenant Guest** and **Server Administrator** permission.       |                       |                                                                                                                              |
   +--------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+

:ref:`Table 2 <esw_pd_0007__table2082345813431>` lists the common operations supported by system-defined identity policies for Enterprise Switch.

.. _esw_pd_0007__table2082345813431:

.. table:: **Table 2** Common operations supported by system-defined identity policies

   +--------------------------------+--------------------+-------------------+----------------+---------------+
   | Operation                      | VPC ReadOnlyAccess | VPC Administrator | VPC FullAccess | Tenant Guest  |
   +================================+====================+===================+================+===============+
   | Creating an enterprise switch  | Not supported      | Supported         | Not supported  | Not supported |
   +--------------------------------+--------------------+-------------------+----------------+---------------+
   | Modifying an enterprise switch | Not supported      | Supported         | Not supported  | Not supported |
   +--------------------------------+--------------------+-------------------+----------------+---------------+
   | Deleting an enterprise switch  | Not supported      | Supported         | Not supported  | Not supported |
   +--------------------------------+--------------------+-------------------+----------------+---------------+
   | Viewing an enterprise switch   | Not supported      | Supported         | Not supported  | Supported     |
   +--------------------------------+--------------------+-------------------+----------------+---------------+
   | Creating a Layer 2 connection  | Not supported      | Supported         | Not supported  | Not supported |
   +--------------------------------+--------------------+-------------------+----------------+---------------+
   | Modifying a Layer 2 connection | Not supported      | Supported         | Not supported  | Not supported |
   +--------------------------------+--------------------+-------------------+----------------+---------------+
   | Deleting a Layer 2 connection  | Not supported      | Supported         | Not supported  | Not supported |
   +--------------------------------+--------------------+-------------------+----------------+---------------+
   | Viewing a Layer 2 connection   | Not supported      | Supported         | Not supported  | Supported     |
   +--------------------------------+--------------------+-------------------+----------------+---------------+
   | Viewing specifications         | Not supported      | Supported         | Not supported  | Supported     |
   +--------------------------------+--------------------+-------------------+----------------+---------------+
   | Viewing quotas                 | Not supported      | Supported         | Not supported  | Supported     |
   +--------------------------------+--------------------+-------------------+----------------+---------------+
   | Viewing the AZ                 | Not supported      | Supported         | Not supported  | Supported     |
   +--------------------------------+--------------------+-------------------+----------------+---------------+
   | Binding a virtual IP address   | Not supported      | Supported         | Not supported  | Not supported |
   +--------------------------------+--------------------+-------------------+----------------+---------------+
   | Unbinding a virtual IP address | Not supported      | Supported         | Not supported  | Not supported |
   +--------------------------------+--------------------+-------------------+----------------+---------------+
