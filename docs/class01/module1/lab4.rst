Lab 1.4 - Deploy Application using Imperative API Calls
---------------------------------------------------------

In this lab, we will build a basic LTM Config using the iControl Rest API.

Task 1 - Deploy a basic HTTP application Virtual Server and associated components.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Deploy

   -  LTM Node

   -  LTM HTTP Monitor

   -  LTM Pool

   -  LTM HTTP Profile

   -  LTM Virtual Server

Perform the following steps to complete this task:

#. Expand ``Lab 1.4 - Deploy Application using Imperative API Calls`` folder in the Postman collection:

   |lab-14-1|

#. Click ``Step 1: Create LTM Node1``. Examine the URL and JSON :guilabel:`Body`. We will send a ``POST`` to the ``/mgmt/tm/ltm/node`` endpoint. Click the :guilabel:`Send` button.

   |lab-14-2|

#. Click ``Step 2: Create LTM Node2``.

#. Click ``Step 3: Get LTM Node`` request in the folder and click the :guilabel:`Send` button.  Examine the node configuration just created.

#. Click ``Step 4: Create LTM Pool``.

    .. NOTE:: Notice this command will fail with a ``400 Bad Request`` because of the missing HTTP monitor object.  Order of operations matter when working with iControl REST API.

    |lab-14-3|

#. Click ``Step 5: Create LTM Monitor``. Examine the URL and JSON :guilabel:`Body`. We will send a ``POST`` to the ``/mgmt/tm/ltm/monitor`` endpoint. Click the :guilabel:`Send` button.

   |lab-14-4|

#. Click ``Step 6: Get LTM Monitor`` request in the folder and click the :guilabel:`Send` button.

    .. NOTE:: The above API endpoint will return all HTTP monitors.  To return only the monitor created in step 3, you can append the specific HTTP resource to the API endpoint.   ``/mgmt/tm/ltm/monitor/Lab1.4_monitor``

#. Click ``Step 7: Create LTM Pool``. Examine the URL and JSON :guilabel:`Body`. We will send a ``POST`` to the ``/mgmt/tm/ltm/pool`` endpoint. Click the :guilabel:`Send` button.

   |lab-14-5|

#. Click ``Step 8: Get LTM Pool`` request in the folder and click the :guilabel:`Send` button.

#. Click ``Step 9: Create LTM HTTP Profile (HTTP)``. Examine the URL and JSON :guilabel:`Body`. We will send a ``POST`` to the ``/mgmt/tm/ltm/profile/http/`` endpoint. Click the :guilabel:`Send` button.

   |lab-14-6|

#. Click ``Step 9: Create LTM HTTP Profile (HTTP)`` again. Click the :guilabel:`Send` button.

    .. NOTE:: Notice the response ``409 Conflict`` response code.  This REST object already exists and is non-idempotent, meaning, a POST to this object cannot overwrite the existing configuration.  The PATCH method would need to be used to update this object.

#. Click ``Step 10: Create LTM HTTP Profile (HTTPS)``. Examine the URL and JSON :guilabel:`Body`. We will send a ``POST`` to the ``/mgmt/tm/ltm/profile/http/`` endpoint. Click the :guilabel:`Send` button.

   |lab-14-7|

#. Click ``Step 11: Get LTM HTTP Profile (HTTP)`` request in the folder and click the :guilabel:`Send` button.

   |lab-14-8|

#. Click ``Step 12: Create LTM SSL Profile ``. Examine the URL and JSON :guilabel:`Body`. We will send a ``POST`` to the ``/mgmt/tm/ltm/profile/client-ssl/`` endpoint. Click the :guilabel:`Send` button.

   |lab-14-9|

#. Click ``Step 13: Get LTM SSL Profile`` request in the folder and click the :guilabel:`Send` button.

   |lab-14-10|

#. Click ``Step 14: Create LTM Virtual Server (80)``. Examine the URL and JSON :guilabel:`Body`. We will send a ``POST`` to the ``/mgmt/tm/ltm/virtual`` endpoint. Click the :guilabel:`Send` button.

   |lab-14-11|

#. Click ``Step 15: Create LTM Virtual Server (443)``. Examine the URL and JSON :guilabel:`Body`. We will send a ``POST`` to the ``/mgmt/tm/ltm/virtual`` endpoint. Click the :guilabel:`Send` button.

   |lab-14-12|

#. Click ``Step 16: Get LTM Virtual Server `` request in the folder and click the :guilabel:`Send` button.

    Perform the following steps to save the system configuration before licensing the device:

#. Click the ``Step 17: Save config`` item in the collection. Click the ``Send`` button to save the BIG-IP configuration. Click the :guilabel:`Send` button.

Task 2 - Verify and Test Virtual Server Deployment.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In this section we will verify the Virtual Server deployment through the TMUI and access the applicaiton using Chrome.

#. Open Google Chrome, navigate to the the **Programmability** folder and select the ``BIG-IP A GUI`` link (or navigate to https://10.1.1.7/).

   |lab-3-71|

#. Authenticate to the interface using the default credentials (``admin/admin.F5demo.com``).

#. Review the **Virtual Servers** configured by navigating to **Local Traffic**, **Virtual Servers**.

   |lab-14-13|

#. Open Google Chrome, navigate to the the **Programmability** folder and select the ``Module 1 VIP01`` link (or navigate to https://10.1.10.120/).

   |lab-14-14|

   .. NOTE:: This applicaiton was deployed with the default BIG-IP SSL certificates.  Bypass any SSL errors when accessing the application.

.. |lab-14-1| image:: images/lab-14-1.png
  :scale: 50%
.. |lab-14-2| image:: images/lab-14-2.png
.. |lab-14-3| image:: images/lab-14-3.png
.. |lab-14-4| image:: images/lab-14-4.png
.. |lab-14-5| image:: images/lab-14-5.png
.. |lab-14-6| image:: images/lab-14-6.png
.. |lab-14-7| image:: images/lab-14-7.png
.. |lab-14-8| image:: images/lab-14-8.png
.. |lab-14-9| image:: images/lab-14-9.png
.. |lab-14-10| image:: images/lab-14-10.png
.. |lab-14-11| image:: images/lab-14-11.png
.. |lab-14-12| image:: images/lab-14-12.png
