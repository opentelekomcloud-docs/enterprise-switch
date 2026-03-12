:original_name: esw_ug_0005.html

.. _esw_ug_0005:

Deleting an Enterprise Switch
=============================

Scenarios
---------

You can delete an enterprise switch to release resources and reduce costs if it is no longer required.

Notes and Constraints
---------------------

An enterprise switch with Layer 2 connections associated cannot be deleted. To delete such an enterprise switch, delete the Layer 2 connections first. For details, see :ref:`Deleting a Layer 2 Connection <esw_ug_0010>`.

.. _esw_ug_0005__section1679132504520:

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner of the page to open the service list and choose **Network** > **Enterprise Switch**.

   The **Enterprise Switch** page is displayed.

4. Click the name of the target enterprise switch.

   The enterprise switch details page is displayed.

5. In the upper right corner of the enterprise switch details page, click **Delete**.

   A confirmation dialog box is displayed.

6. Click **OK**.

   This operation takes 10 to 60 seconds to complete. If the **Delete** button is staying inactive after the Layer 2 connections are deleted, refresh the page.

.. |image1| image:: /_static/images/en-us_image_0000002007326742.png
.. |image2| image:: /_static/images/en-us_image_0000002524317986.png
