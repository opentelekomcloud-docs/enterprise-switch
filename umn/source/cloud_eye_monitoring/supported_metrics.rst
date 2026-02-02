:original_name: esw_ug_0014.html

.. _esw_ug_0014:

Supported Metrics
=================

Description
-----------

This section describes metrics reported by enterprise switches to Cloud Eye as well as their namespaces, metrics, and dimensions. You can use the Cloud Eye management console or APIs to obtain the metrics and alarms generated for enterprise switches.

Namespace
---------

SYS.ESW

Monitoring Metrics
------------------

With Cloud Eye, you can monitor the network status of enterprise switches.

.. table:: **Table 1** Enterprise switch metrics

   +--------------------+--------------------+---------------------------------------------------------------+-------------+-------+-----------------+------------------------------+--------------------------------+
   | ID                 | Name               | Description                                                   | Value Range | Unit  | Conversion Rule | Monitored Object (Dimension) | Monitoring Interval (Raw Data) |
   +====================+====================+===============================================================+=============+=======+=================+==============================+================================+
   | outbound bandwidth | Outbound Bandwidth | Network traffic per second going out of the enterprise switch | >= 0        | bit/s | 1024 (IEC)      | instance_id                  | 1 minute                       |
   +--------------------+--------------------+---------------------------------------------------------------+-------------+-------+-----------------+------------------------------+--------------------------------+
   | inbound bandwidth  | Inbound Bandwidth  | Network traffic per second going into the enterprise switch   | >= 0        | bit/s | 1024 (IEC)      | instance_id                  | 1 minute                       |
   +--------------------+--------------------+---------------------------------------------------------------+-------------+-------+-----------------+------------------------------+--------------------------------+
   | outbound traffic   | Outbound Traffic   | Network traffic going out of the enterprise switch            | >= 0        | byte  | 1024 (IEC)      | instance_id                  | 1 minute                       |
   +--------------------+--------------------+---------------------------------------------------------------+-------------+-------+-----------------+------------------------------+--------------------------------+
   | inbound traffic    | Inbound Traffic    | Network traffic going into the enterprise switch              | >= 0        | byte  | 1024 (IEC)      | instance_id                  | 1 minute                       |
   +--------------------+--------------------+---------------------------------------------------------------+-------------+-------+-----------------+------------------------------+--------------------------------+
   | outbound pps       | Outbound PPS       | Packets per second going out of the enterprise switch         | >= 0        | pps   | N/A             | instance_id                  | 1 minute                       |
   +--------------------+--------------------+---------------------------------------------------------------+-------------+-------+-----------------+------------------------------+--------------------------------+
   | inbound pps        | Inbound PPS        | Packets per second going into the enterprise switch           | >= 0        | pps   | N/A             | instance_id                  | 1 minute                       |
   +--------------------+--------------------+---------------------------------------------------------------+-------------+-------+-----------------+------------------------------+--------------------------------+

Dimensions
----------

The metric measurement dimension of an enterprise switch is **instance_id**.

=========== =====================
Key         Value
=========== =====================
instance_id Enterprise switch ID.
=========== =====================
