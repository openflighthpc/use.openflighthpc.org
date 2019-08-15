.. _gridware-perl:

Working with Gridware Applications: Perl
========================================

The following guide will detail the installation of Perl, along with some of the advanced features of Alces Gridware when working with the Perl Gridware package. 

Perl Installation
-------------------

Many different versions of Perl are available through the Alces Gridware utility - you can see the list of available packages with the ``flight gridware search`` function, for example: 

.. code:: bash

    [centos@gateway1(scooby) ~]$ flight gridware search --name perl
    main/apps/perl/5.20.2      main/libs/bioperl/1.6.923

To install, for example - Perl version 5.20.2; run the following command: 

.. code:: bash

    [centos@gateway1(scooby) ~]$ flight gridware install apps/perl/5.20.2
    Preparing to install main/apps/perl/5.20.2
    Installing main/apps/perl/5.20.2
    Importing apps-perl-5.20.2-el7.tar.gz
    
     > Fetching archive
            Download ... OK
    
     > Preparing import
             Extract ... OK
              Verify ... OK
    
     > Processing apps/perl/5.20.2/gcc-4.8.5
           Preparing ... OK
           Importing ... OK
         Permissions ... OK
    
     > Finalizing import
              Update ... OK
        Dependencies ... OK
    
    Installation complete.


Once the compilation has finished - the Perl 5.20.2 Gridware package will be available for use; check its availability and load using: 

.. code:: bash

    [centos@gateway1(scooby) ~]$ module avail
    ---  /opt/gridware/local/el7/etc/modules  ---
      apps/perl/5.20.2/gcc-4.8.5
    [centos@gateway1(scooby) ~]$ module load apps/perl
    apps/perl/5.20.2/gcc-4.8.5
     | -- libs/gcc/system ... SKIPPED (already loaded)
     |
     OK
    [centos@gateway1(scooby) ~]$ perl --version
    This is perl 5, version 16, subversion 3 (v5.16.3) built for x86_64-linux-thread-multi 
    
Multiple versions of a package can exist at one time, however only one version of a particular application module can be loaded at any one time. To load a different version of Perl: 

.. code:: bash

    [centos@gateway1(scooby) ~]$ flight module load apps/perl/5.18.0/gcc-4.8.5
    apps/perl/5.18.0/gcc-4.8.5 ... VARIANT (have alternative: apps/perl/5.20.2/gcc-4.8.5)
    [centos@gateway1(scooby) ~]$ flight module unload apps/perl/5.20.2/gcc-4.8.5
                  apps/perl/5.20.2/gcc-4.8.5 ... UNLOADING --> OK
    [centos@gateway1(scooby) ~]$ flight module load apps/perl/5.18.0/gcc-4.8.5
    apps/perl/5.18.0/gcc-4.8.5
     | -- libs/gcc/system ... SKIPPED (already loaded)
     |
     OK
    [centos@gateway1(scooby) ~]$ perl --version
    This is perl 5, version 18, subversion 0 (v5.18.0) built for x86_64-linux

Installation of language libraries
----------------------------------

Through the Alces Gridware utility, installation of lanaguage libraries is possible both on a system-wide level, and also on a per-user basis. The following section details both system-wide language library installation, as well as user-level language library installation. 

System-wide language libraries: Perl
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

As the ``centos`` administrator user, or any other sudo enabled user that can switch to root - change to the ``root`` user account.

Next, load the version of Perl you wish to add language libraries to - for example ``perl/5.20.2``

.. code:: bash

    [root@gateway1(scooby) ~]# module load apps/perl/5.20.2
    apps/perl/5.20.2/gcc-4.8.5
     | -- libs/gcc/system
     |    * --> OK
     |
     OK

Next - use the ``cpan`` utility to install the Perl libraries you, or additional system users require - for example: 

.. code:: bash

    [root@gateway1(scooby) ~]# cpan Date::Simple
    Fetching with Net::FTP:
    ftp://cpan.etla.org/pub/CPAN/authors/01mailrc.txt.gz
    Reading '/opt/gridware/share/perl/5.20.2/cpan/sources/authors/01mailrc.txt.gz'
    <--snip-->

The ``Date::Simple`` module will now be available to any system user loading the ``Perl 5.20.2`` Gridware package. 

To verify successful installation, switch to a non-root user; for example ``centos`` will now be able to see and use the ``Date::Simple`` module: 

.. code:: bash

    [centos@gateway1(scooby) ~]$ module load apps/perl/5.20.2
    apps/perl/5.20.2/gcc-4.8.5
     | -- libs/gcc/system
     |    * --> OK
     |
     OK
    [centos@gateway1(scooby) ~]$ cpan -l 2>&1 | grep Date::Simple | head -n1
    Date::Simple	3.03


User-specific language libraries: Perl
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Users may also wish to install their own language libraries, these will be unavailable to other users of the environment. 

As the user you wish to install a Perl module for, load the ``perl`` Gridware application, then use ``cpan`` to install the required module: 

.. code:: bash

    [centos@gateway1(scooby) ~]$ cpan File::Slurp
    Fetching with Net::FTP:
    ftp://cpan.etla.org/pub/CPAN/authors/01mailrc.txt.gz
    Reading '/home/barney/gridware/share/perl/5.20.2/cpan/sources/authors/01mailrc.txt.gz'
    <-- snip -->
    [centos@gateway1(scooby) ~]$ cpan File::Slurp
    Reading '/home/barney/gridware/share/perl/5.20.2/cpan/Metadata'
      Database was generated on Fri, 19 Feb 2016 02:41:02 GMT
    File::Slurp is up to date (9999.19).

The ``File::Slurp`` installation was successful - and we can now use it as the ``centos`` user. Switching to another user will confirm the user-level installation success; the ``root`` user will not be able to use the ``File::Slurp`` Perl module, requiring the module be installed again: 

.. code:: bash

    [root@gateway1(scooby) ~]# flight module load apps/perl/5.20.2
    [root@gateway1(scooby) ~]# cpan File::Slurp
    Fetching with Net::FTP:
    ftp://cpan.etla.org/pub/CPAN/authors/01mailrc.txt.gz
    Reading '/home/centos/gridware/share/perl/5.20.2/cpan/sources/authors/01mailrc.txt.gz'
