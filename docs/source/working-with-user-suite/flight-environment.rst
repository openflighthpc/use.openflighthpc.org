.. _flight-environment:

Flight Environment
==================

Viewing Available Ecosystems
----------------------------

Various :ref:`package-ecosystems` are available for managing software on your Flight research environment. These can be viewed by using the ``env`` subcommand::

    [flight@gateway1 (scooby) ~]$ flight env avail


Creating a Local Ecosystem
--------------------------

A local ecosystem is only available to the user that creates it. All of the packages and libraries are installed to the users home directory.

To install a package ecosystem, use the create command as follows (replacing gridware with your desired package ecosystem)::

    [flight@gateway1 (scooby) ~]$ flight env create gridware

Once a package ecosystem has been installed, it needs to be activated for the session to be able to manage software with it::

    [flight@gateway1 (scooby) ~]$ flight env activate gridware
    <gridware> [flight@gateway1 (scooby) ~]$

.. tip:: Your preferred software ecosystem can be set to automatically activate for your user within the flight system by running ``flight env set-default gridware``, replacing gridware with your chosen software ecosystem

Creating a Global Ecosystem
---------------------------

A global ecosystem is available to all users on the system. All of the packages and libraries are installed to a shared storage directory. The global directories can be configured in ``/opt/flight/opt/flight-env/etc/config.yml`` with the ``global_depot_path:`` and ``global_build_cache_path`` keys.

.. note:: The user requires suitable write permissions to the configured global depot paths in order to be able to create a global ecosystem

To install a global package ecosystem, use the create command with the global option flag::

    [root@gateway1 (scooby) ~]$ flight env create -g gridware

Once the global ecosystem has been installed, it needs to be activated for the session to be able to monitor software with it::

    [root@gateway1 (scooby) ~]$ flight env activate gridware@global
    <gridware@global> [flight@gateway1 (scooby) ~]$

.. _custom-ecosystem-names:

Custom Ecosystem Names
----------------------

When installing an ecosystem, an custom alias can be added by appending ``@mycustomname`` to the end of creation command. For example, to create a local gridware installation with the alias ``test``::

    [flight@gateway1 (scooby) ~]$ flight env create gridware@test

To activate this environment, the alias will need to be specified in the activation command::

    [flight@gateway1 (scooby) ~]$ flight env activate gridware@test
    <gridware@test> [flight@gateway1 (scooby) ~]$

