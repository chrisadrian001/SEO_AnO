Module 1: Imperative Automation with the BIG-IP and iControl Rest
=================================================================

In this module, you will learn the basic concepts required to interact
with the BIG-IP iControl REST API. Additionally, you will walk through steps
commonly used during a Device Onboarding workflow to deploy a fully functional
BIG-IP. It is important to note that this module will
focus on demonstrating an **Imperative** approach to automation.

.. NOTE:: In order to confirm the results of REST API calls made in this lab,
   it is recommended to keep GUI/SSH sessions to the BIG-IP device open. By
   default, BIG-IP will log all the REST API related events locally to
   **restjavad.0.log**. These logs can also be directed to a remote Syslog
   server (see https://support.f5.com/csp/article/K13080). On a side note, the
   **LTM** log files listed below contain log messages specific to  BIG-IP
   local traffic management events.

   - BIG-IP:

     - /var/log/ltm
     - /var/log/restjavad.0.log

.. toctree::
   :maxdepth: 1
   :glob:

   lab*
