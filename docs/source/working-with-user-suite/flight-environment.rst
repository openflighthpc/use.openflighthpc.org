.. _flight-environment:

Flight Environment
==================

Working with Package Ecosystems
-------------------------------

Various :ref:`package-ecosystems` are available for managing software on your Flight research environment. These can be installed using the ``env`` subcommand::

    [flight@gateway1 (scooby) ~]$ flight env create gridware

Once a package ecosystem has been installed, it needs to be activated for the session to be able to manage software with it::

    [flight@gateway1 (scooby) ~]$ flight env activate gridware
    <gridware> [flight@gateway1 (scooby) ~]$

.. tip:: Your preferred software ecosystem can be set to automatically activate for your user within the flight system by running ``flight env set-default gridware``, replacing gridware with your chosen software ecosystem

