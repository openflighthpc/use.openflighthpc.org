.. _install-web:

Flight Web Suite
================

What is Flight Web Suite?
--------------------------

The Flight Web Suite is a collection of web applications that provide users with easy and intuitive ways to interact with their research environment. The purpose of these tools is to get researchers started with HPC as quickly as possible without needing to worry about configuring system access and desktop session creation, leaving them to do what they do best - research!

Flight Web Suite is made up of the following tools:

- WWW: Flight WWW provides a standalone NGINX server preconfigured to host the various web suite applications
- Certbot: Flight Certbot provides helper tools for
- Service: Flight Service provides management of the various web applications and services
- Console WebApp/API: The API & web application for accessing terminals via a browser
- Desktop WebApp/API: The API & web application for creating, managing & using desktops via a browser

Installing Flight Web Suite
----------------------------

The OpenFlight project packages tools as both RPMs and debs that are hosted in package repositories which can be quickly installed with a couple of commands. 

Before proceeding, ensure that :ref:`the Flight User Suite is installed <install-user>`.


Installation Method 1: Quick
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The quickest and simplest way to get up and running with the user suite is to simply install the group package for the tools. This will ensure that compatible versions of all the tools are installed.

.. tabs::

    .. group-tab:: CentOS 7

        - Install the web suite RPM::

            [flight@gateway1 ~]$ sudo yum install flight-web-suite

        - Install extra packages (note: the EPEL repository is required for the websockify package)::

            [flight@gateway1 ~]$ sudo yum install python-websockify xorg-x11-apps netpbm-progs

    .. group-tab:: CentOS 8

        - Install the web suite RPM::

            [flight@gateway1 ~]$ sudo dnf install flight-web-suite

        - Install extra packages (note: the PowerTools repository is required for the xorg-x11-apps package)::

            [flight@gateway1 ~]$ sudo dnf install python3-websockify xorg-x11-apps netpbm-progs

    .. group-tab:: Ubuntu 18.04

        - Install the web suite deb::

            flight@gateway1:~$ sudo apt-get install flight-web-suite

        - Install extra packages::

            flight@gateway1:~$ sudo apt-get install netpbm x11-apps websockify

    .. group-tab:: Ubuntu 20.04

        - Install the web suite deb::

            flight@gateway1:~$ sudo apt-get install flight-web-suite

        - Install extra packages::

            flight@gateway1:~$ sudo apt-get install netpbm x11-apps websockify

Installation Method 2: Manual
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

For those who wish to have more control over their installation, all of the Flight User Suite tools have manual installation instructions in the READMEs on GitHub.

- Flight WWW - https://github.com/openflighthpc/openflight-omnibus-builder/tree/master/builders/flight-www 
- Flight Certbot - https://github.com/openflighthpc/openflight-omnibus-builder/tree/master/builders/flight-certbot
- Flight Service - https://github.com/openflighthpc/openflight-omnibus-builder/tree/master/builders/flight-service
- Flight Console API - https://github.com/openflighthpc/flight-console-api#installation
- Flight Console WebApp - https://github.com/openflighthpc/flight-console-webapp#installation
- Flight Desktop API - https://github.com/openflighthpc/flight-desktop-restapi#installation
- Flight Desktop WebApp - https://github.com/openflighthpc/flight-desktop-webapp#installation

Configuring Web Suite
---------------------

System Prerequisites
^^^^^^^^^^^^^^^^^^^^

In order to authenticate the user in the web interface, the following must be true:
- User has a password (can be set with the ``passwd`` command or through other user management software that is setup on the system)
- Ports 80 & 443 on the gateway must be accessible (allowed through both the system firewall and cloud security group)
- SSH password authentication must be enabled (can be set in ``/etc/ssh/sshd_config`` in CentOS or through other access management software that is setup on the system)

Certificate Preparation
^^^^^^^^^^^^^^^^^^^^^^^

To secure the server connections, it is recommended to generate a certificate to be used by the web suite. The Flight Web Suite comes with tools that can generate either a "self-signed" or LetsEncrypt certificate. Alternatively, a certificate that has been created outside of the web suite can be used to secure the server.

Self-Signed
~~~~~~~~~~~

A self-signed certificate, whilst not usually trusted by browsers, does still provide extra security to the web server over HTTP communication.

To generate and install the self-signed certificates, simply::

    [flight@gateway1(scooby) ~]$ flight www cert-gen --cert-type self-signed --domain $(hostname -d)

After this has run, the HTTPS server can be enabled with::

    [flight@gateway1(scooby) ~]$ flight www enable-https

Lets Encrypt
~~~~~~~~~~~~

To generate and install a Lets Encrypt certificate, run the following (replacing the domain and email with appropriate values)::

    [flight@gateway1(scooby) ~]$ flight www cert-gen --cert-type lets-encrypt --domain gateway1.scooby.example.com --email user@example.com

.. note:: A DNS record for the chosen domain name, pointing to the IP of the gateway, will need to be setup with your DNS provider in order for certificate generation to work

After this has run, the HTTPS server can be enabled with::

    [flight@gateway1(scooby) ~]$ flight www enable-https


External Certificate
~~~~~~~~~~~~~~~~~~~~

Externally generated certificates can be used by placing them in ``/opt/flight/etc/www/ssl/``, the files that should be in there are:

- ``fullchain.pem``: The full certificate (recommended permissions are 644 root:root)
- ``key.pem``: The private key for the certificate (recommended permissions are 644 root:root)

After placing the certificates in place, the HTTPS server can be enabled with::

    [flight@gateway1(scooby) ~]$ flight www enable-https

Console Configuration
^^^^^^^^^^^^^^^^^^^^^

Before the terminal web service can be used it will need to be configured, an interactive configuration prompt is available with::

    [flight@gateway1(scooby) ~]$ flight service configure console-webapp

The information requested in the configuration prompt are:

- Cluster Name: The name of the cluster, to be displayed in the login page for the web front-end
- Cluster Description: An optional description that is shown below the cluster name in the web front-end
- Cluster Logo: A URL to an image to be used in the web front-end 
- Hostname or IP: The hostname or IP address of the gateway that is world-reachable for web access

Desktop Configuration
^^^^^^^^^^^^^^^^^^^^^

Before the desktop web service can be used it will need to be configured, an interactive configuration prompt is available with::

    [flight@gateway1(scooby) ~]$ flight service configure desktop-webapp

The information requested in the configuration prompt are:

- Cluster Name: The name of the cluster, to be displayed in the login page for the web front-end
- Cluster Description: An optional description that is shown below the cluster name in the web front-end
- Cluster Logo: A URL to an image to be used in the web front-end 
- Hostname or IP: The hostname or IP address of the gateway that is world-reachable for web access

