.. _flight-system:

Flight System
=============

.. _activate-flight-system:

Activating the Flight System
----------------------------

The Flight User Suite sits unobtrusively on the research environment with the `flight` command serving as an entrypoint to the various system commands.

This provides some quick tips to activating the system and finding out more about the flight system (``flight info``).

To load the system, simply run ``flight start`` (which, when first run, will generate some login keys for allowing passwordless login to compute nodes)

.. image:: flightenv.png
    :alt: Activating the flight system

.. tip:: The flight system can be set to automatically start on login for the user by running ``flight set always on``

