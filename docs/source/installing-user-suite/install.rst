.. _install:

What is Flight User Suite?
--------------------------

The Flight User Suite is a collection of environment tools that provide users with easy and intuitive ways to manage the software and desktop sessions in a research envrionment. The purpose of these tools is to get researchers started with HPC as quickly as possible without needing to worry about their environment, leaving them to do what they do best - research!

The tools are non-intrusive to the research environment, defaulting to a "deactivated" state. Leaving admins and users free to configure and utilise their systems how they want.

Flight User Suite is made up of the following tools:

- Runway: Flight Runway provides a self-contained Ruby environment and an entrypoint for accessing the other flight tools
- Env: Flight Env provides access to, and management of, various software managers to ensure access to a wide variety of HPC applications
- Desktop: Flight Desktop provides an intuitive tool for launching VNC-ready virtual desktops of many different desktop environments (gnome, xterm, kde, etc)
- Starter: Flight Starter provides profile scripts for integrating the user suite into the shell environment

Installing Flight User Suite
----------------------------

The OpenFlight project packages tools as RPMs and hosts them in a yum repository that can be quickly installed via a release RPM. 

Adding the OpenFlight Yum Repositories
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- Install the OpenFlight release RPM::

    [flight@gateway1 ~]$ yum install https://repo.openflighthpc.org/openflight/centos/7/x86_64/openflighthpc-release-2-1.noarch.rpm

- Rebuild the yum cache::

    [flight@gateway1 ~]$ yum makecache

Now the OpenFlight repositories are installed. There are 3 repositories available - production (enabled by default), dev (providing development releases of tools) and vault (access to old, unsupported versions and retired tools).


Installation Method 1: Quick
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The quickest and simplest way to get up and running with the user suite is to simply install the group package for the tools. This will ensure that compatible versions of all the tools are installed.

- Install the user suite RPM::

    [flight@gateway1 ~]$ yum install flight-user-suite

.. note:: After installation, either reboot your system or logout and back in again to expose the `flight` command to the shell

Installation Method 2: Slightly Less Quick
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Each tool in the user suite is also available through the repositories and can be installed one at a time.

- Install the Flight Runway RPM::

    [flight@gateway1 ~]$ yum install flight-runway

- Install Flight Env RPM::

    [flight@gateway1 ~]$ yum install flight-env

- Install Flight Desktop RPM::

    [flight@gateway1 ~]$ yum install flight-desktop

- Install Flight Starter RPM::

    [flight@gateway1 ~]$ yum install flight-starter

.. note:: After installation, either reboot your system or logout and back in again to expose the `flight` command to the shell

Installation Method 3: Manual
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

For those who wish to have more control over their installation, all of the Flight User Suite tools have manual installation instructions in the READMEs on GitHub.

- Flight Runway - https://github.com/openflighthpc/flight-runway#manual-installation
- Flight Env - https://github.com/openflighthpc/flight-env#installation
- Flight Desktop - https://github.com/openflighthpc/flight-desktop#from-source
- Flight Starter - https://github.com/openflighthpc/flight-starter#installation
