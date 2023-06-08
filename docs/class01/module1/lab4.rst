Lab 1.4 - Deploy Application using Imperative API Calls
---------------------------------------------------------

In this lab, we will build a basic LTM Config using the iControlRest API.

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

#. Click ``Step 1: Create LTM Node``. Examine the URL and JSON :guilabel:`Body`. We will send a ``POST`` to the ``/mgmt/tm/ltm/node`` endpoint.

   |lab-14-2|

#. Click ``Step 2: Get LTM Node`` request in the folder and click the :guilabel:`Send` button.  Examine the node configuration just created.

#. Click ``Step 3: Create LTM Pool``.

#. Notice this command will fail because of the missing HTTP monitor object.  Order of operations matter when working with the imperative iControl API.

#. Click ``Step 4: Create LTM Monitor``. Examine the URL and JSON :guilabel:`Body`. We will send a ``POST`` to the ``/mgmt/tm/ltm/monitor`` endpoint.

   |lab-14-3|

#. Click ``Step 5: Get LTM Monitor`` request in the folder and click the :guilabel:`Send` button.

.. NOTE:: The above API endpoint will return all HTTP monitors.  To return only the monitor created in step 3, you can append
   the specific HTTP resource to the API endpoint.   ``/mgmt/tm/ltm/monitor/Lab1.4_monitor``

#. Click ``Step 6: Create LTM Pool``. Examine the URL and JSON :guilabel:`Body`. We will send a ``POST`` to the ``/mgmt/tm/ltm/pool`` endpoint.

   |lab-14-4|

#. Click ``Step 7: Get LTM Pool`` request in the folder and click the :guilabel:`Send` button.

#. Click ``Step 8: Create LTM HTTP Profile (HTTP)``. Examine the URL and JSON :guilabel:`Body`. We will send a ``POST`` to the ``/mgmt/tm/ltm/profile/http/`` endpoint.

   |lab-14-5|

#. Click ``Step 9: Get LTM HTTP Profile (HTTP)`` request in the folder and click the :guilabel:`Send` button.

#. Click ``Step 8: Create LTM HTTP Profile (HTTP)`` again.

#. Notice the response code of 404.  This object already exists and iControl REST is non-idempotent, meaning, a POST to an already existing object will fail.

#. Click ``Step 10: Create LTM Virtual Server (80)``. Examine the URL and JSON :guilabel:`Body`. We will send a ``POST`` to the ``/mgmt/tm/ltm/virtual`` endpoint.

   |lab-14-6|

#. Click ``Step 11: Get LTM Virtual Server (80)`` request in the folder and click the :guilabel:`Send` button.

Perform the following steps to save the system configuration before licensing the device:

#. Click the ``Step 12: Save config`` item in the collection. Click the ``Send`` button to save the BIG-IP configuration.

.. |lab-14-1| image:: images/lab-14-1.png
.. |lab-14-2| image:: images/lab-14-2.png
.. |lab-14-3| image:: images/lab-14-3.png
.. |lab-14-4| image:: images/lab-14-4.png
.. |lab-14-5| image:: images/lab-14-5.png
.. |lab-14-6| image:: images/lab-14-6.png
