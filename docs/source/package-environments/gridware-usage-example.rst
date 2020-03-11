.. _gridware-usage-example:

Gridware: Usage Example
=======================

Creating and Using Environment
------------------------------

Flight Env provides quick setup methods to create a gridware software environment. 

To install and use gridware:

- :ref:`Activate the flight system <activate-flight-system>`
- Create the gridware installation for the user::

    [flight@gateway1 ~]$ flight env create gridware
    Creating environment gridware@default
       > ✅ Verifying prerequisites
       > ✅ Fetching prerequisite (modules)
       > ✅ Extracting prerequisite (modules)
       > ✅ Building prerequisite (modules)
       > ✅ Installing prerequisite (modules)
       > ✅ Fetching prerequisite (gridware)
       > ✅ Extracting prerequisite (gridware)
       > ✅ Installing prerequisite (gridware)
       > ✅ Configuring repo: main
       > ✅ Configuring repo: volatile
       > ✅ Creating environment (gridware@default)
    Environment gridware@default has been created

- Activate the gridware environment::

    [flight@gateway1 ~]$ flight env activate gridware
    <gridware> [flight@gateway1 ~]$

- Check that gridware can be run::

    <gridware> [flight@gateway1 ~]$ gridware --version
    gridware 1.5.1


Installing and Running Perl
---------------------------

An example workflow using perl is demonstrated below.

- View available versions::

    <gridware> [flight@gateway1 ~]$ gridware search
    2 repositories need to update ...
    Updating repository: main
              Update ... OK (At: 55916fd)
    Updating repository: volatile
              Update ... OK (At: 61cc544)
    main/apps/bismark/0.16.3                  main/apps/bismark/0.17.0                  main/apps/cegma/2.5.0
    main/apps/clusterflow/0.6.0-20170502      main/apps/clusterflow/0.6.0-20170530      main/apps/forks/0.36
    main/apps/ihrsr/1.5                       main/apps/perl/5.20.2                     main/apps/python/2.7.8
    <-- snip -->
    volatile/apps/perl/5.16.1                 volatile/apps/perl/5.16.3                 volatile/apps/perl/5.18.0
    volatile/apps/perl/5.20.2                 volatile/apps/python/2.7.3                volatile/apps/python/2.7.5
    <-- snip -->

- Install specific version::

    <gridware> [flight@gateway1 ~]$ gridware install main/apps/perl/5.20.2
    Preparing to install main/apps/perl/5.20.2
    Installing main/apps/perl/5.20.2

     > Preparing package sources
            Download --> perl-5.20.2.tar.gz ... OK
              Verify --> perl-5.20.2.tar.gz ... OK
            Packaged --> CPAN-Config.pm     ... OK
            Packaged --> CPAN-MyConfig.pm   ... OK

     > Preparing for installation
               Mkdir ... OK (/home/flight/.cache/flight/env/build/gridware/src/apps/perl/5.20.2/gcc-4.8.5)
             Extract ... OK

     > Proceeding with installation
             Compile ... OK
               Mkdir ... OK (/home/flight/.local/share/flight/env/gridware+default/depots/23cd1570/el7/pkg/apps/perl/5.20.2/gcc-4.8.5)
             Install ... OK
              Module ... OK

    Installation complete.


- Check installation location::

    <gridware> [flight@gateway1 ~]$ module load apps/perl
    apps/perl/5.20.2/gcc-4.8.5
     | -- libs/gcc/system
     |    * --> OK
     |
     OK
    <gridware> [flight@gateway1 ~]$ which perl
    ~/.local/share/flight/env/gridware+default/depots/23cd1570/el7/pkg/apps/perl/5.20.2/gcc-4.8.5/bin/perl

- Install perl library (this may prompt for initial ``cpan`` configuration, once configuration is complete then the library will be installed)::

    <gridware> [flight@gateway1 ~]$ cpan File::Slurp
    Reading '/home/flight/gridware/share/perl/5.20.2/cpan/Metadata'
      Database was generated on Tue, 10 Sep 2019 01:17:03 GMT
    Running install for module 'File::Slurp'
    <-- snip -->
    Appending installation info to /home/flight/gridware/share/perl/5.20.2/lib/5.20.2/x86_64-linux/perllocal.pod
      CAPOEIRAB/File-Slurp-9999.27.tar.gz
      /usr/bin/make install INSTALLMAN3DIR=/home/flight/gridware/share/perl/5.20.2/man/man3 INSTALLMAN1DIR=/home/flight/gridware/share/perl/5.20.2/man/man1 -- O

- Check installation worked::

    <gridware> [flight@gateway1 ~]$ cpan File::Slurp
    Reading '/home/flight/gridware/share/perl/5.20.2/cpan/Metadata'
      Database was generated on Tue, 10 Sep 2019 01:17:03 GMT
    File::Slurp is up to date (9999.27).

