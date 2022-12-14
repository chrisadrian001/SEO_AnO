Lab 1.4: Basic Network Connectivity
--------------------------------------

This lab will focus on the configuration of the following items:

-  L1-3 Networking

   -  Physical Interface Settings

   -  L2 Connectivity (**VLAN**, VXLAN, etc.)

   -  L3 Connectivity (**Self IPs, Routing**, etc.)

We will specifically cover the items in **BOLD** above in the following
labs. It should be noted that many permutations of the Device Onboarding process exist due to the nature of different organizations. This class is designed to teach enough information so that you can then apply the knowledge learned and help articulate and/or deliver a specific solution for your environment.

The following table and diagram lists the L2-3 network information used to configure connectivity for BIG-IP A:

.. list-table::
   :stub-columns: 1
   :header-rows: 1

   * - **Type**
     - **Name**
     - **Details**
   * - VLAN
     - External
     - **Interface**: 1.1

       **Tag:** 10

   * - VLAN
     - Internal
     - **Interface**: 1.2

       **Tag:** 20

   * - Self IP
     - Self-External
     - **Address**: 10.1.10.7/24

       **VLAN:** External

   * - Self IP
     - Self-Internal
     - **Address**: 10.1.20.7/24

       **VLAN:** Internal
   * - Route
     - Default
     - **Network:** 0.0.0.0/0

       **GW:** 10.1.10.1

Task 1 - Create VLANs
~~~~~~~~~~~~~~~~~~~~~

.. NOTE:: This lab shows how to configure VLAN tags, but does not deploy tagged interfaces.  To use tagged interfaces, the ``tagged`` attribute needs to have the value ``true``.

Perform the following steps to configure the VLAN objects/resources:

#. Expand the ``Lab 1.4 - Basic Network Connectivity`` folder in the Postman collection.

#. Click the ``Step 1: Create a VLAN`` request in the folder. Click :guilabel:`Body` and examine the JSON request body; the values for creating the Internal VLAN have already been populated.

#. Click the :guilabel:`Send` button to create the VLAN

#. **Repeat Step 1**. However, this time, modify the JSON body to create the External VLAN using the parameters shown in the table above. In order to do so you can replace the following:

   - ``name``: ``Internal`` > ``External``
   - ``tag``: ``20`` > ``10``
   - ``interfaces``: ``1.2`` > ``1.1``

   |lab-4-6|

#. Click the ``Step 2: Get VLANs`` request in the folder. Click the :guilabel:`Send` button to ``GET`` the VLAN collection. Examine the response to make sure both VLANs have been created.

Task 2 - Create Self IPs
~~~~~~~~~~~~~~~~~~~~~~~~

Perform the following steps to configure the Self IP objects/resources:

#. Click the ``Step 3: Create Internal Self IP`` request in the folder. Click :guilabel:`Body` and examine the JSON body; the values for creating the Self-Internal Self IP have already been populated.

   .. Warning:: The JSON body sets the VLAN to ``/Common/External`` on purpose. You will modify this value in the steps below.  Please do not change the value.

#. Click the :guilabel:`Send` button to create the Self IP.

#. Click the ``Step 4: Create External Self IP`` request in the folder and click :guilabel:`Send`.

#. Click the ``Step 5: Get Self-Internal Self IP Attributes`` request in the folder and click the :guilabel:`Send` button.  Examine the VLAN settings of the Resource as noted above the Self IP has been assigned to the **wrong** VLAN (intentionally).

   .. NOTE:: Postman can check the responses for specific values to verify if the result of a request is what it is expected to be. The :guilabel:`Test Results` for this request will show a failure for the ``[Check Value] vlan == /Common/Internal`` value.  This is intentional, and you should continue to the next section.

   |lab-4-1|

Task 3 - Modify Existing Self IP Resource
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In order to modify an existing object via the REST API, the URI path has to be changed.  In the previous examples, we used a ``POST`` to create Resources under a Collection. Therefore, the URI used was that of the Collection itself. If you wish to update/modify a Resource, you must refer to the Resource directly.

For example, the Collection URI for Self IPs is  ``/mgmt/tm/net/self``.

The Resource URI for the ``Self-Internal`` Self IP is ``/mgmt/tm/net/self/~Common~Self-Internal``.  Notice that the BIG-IP
partition and object name has been added to the Collection URI for the Resource URI.

#. On the open ``Step 5: Get Self-Internal Self IP Attributes`` request change the request method from ``GET`` to ``PATCH``.  The ``PATCH`` method is used to modify the attributes of an existing Resource.

   |lab-4-5|

#. Copy ``(Ctrl + C)`` the entire JSON **RESPONSE** from the previous ``GET`` request.

   |lab-4-2|

#. Paste ``(Ctrl + V)`` the text into JSON **REQUEST** body:

   .. NOTE:: Be sure to highlight any existing text and replace it while pasting.

   |lab-4-3|

#. In the JSON body change the ``vlan`` attribute to ``/Common/Internal`` and click ``Send``:

   |lab-4-4|

#. Click the ``Step 6: Get Self IPs`` item in the collection. Click the ``Send`` button to GET the Self IP collection. Examine the response to make sure both Self IPs have been created and associated with the appropriate vlan.

Task 4 - Create Routes
~~~~~~~~~~~~~~~~~~~~~~

Perform the following steps to configure the Route object/resource:

#. Before creating the route, we double-check the content of the routing table. Click the ``Step 7: Get Routes`` item in the collection. Click the ``Send`` button to ``GET`` the routes collection. Examine the response to make sure there is no route.

#. Click the ``Step 8: Create a Route`` item in the collection. Click :guilabel:`Body` and examine the JSON body; the values for creating the default route have already been populated.

#. Click the ``Send`` button to create the route.

#. Click the ``Step 9: Get Routes`` item in the collection again. Click the ``Send`` button to ``GET`` the routes collection. Examine the response to make sure the route has been created.

Perform the following steps to save the system configuration before licensing the device:

#. Click the ``Step 10: Save config`` item in the collection. Click the ``Send`` button to save the BIG-IP configuration.

.. Warning:: Configuration changes made through the iControl REST API are not saved by default. A configuration save prior to a reload or reboot of the system is required.

.. |lab-4-1| image:: images/lab-4-1.png
.. |lab-4-2| image:: images/lab-4-2.png
.. |lab-4-3| image:: images/lab-4-3.png
.. |lab-4-4| image:: images/lab-4-4.png
.. |lab-4-5| image:: images/lab-4-5.png
.. |lab-4-6| image:: images/lab-4-6.png
