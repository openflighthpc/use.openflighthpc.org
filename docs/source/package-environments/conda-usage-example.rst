.. _conda-usage-example:

Conda: Usage Example
====================


Creating and Using Environment
------------------------------

Flight Env provides quick setup methods to create a conda software environment. 

To install and use conda:

- :ref:`Activate the flight environment <activate-flight-env>`
- Create the conda installation for the user::

    [flight@gateway1 ~]$ flight env create conda
    Creating environment conda@default
       > ✅ Verifying prerequisites
       > ✅ Fetching prerequisite (miniconda)
       > ✅ Creating environment (conda@default)
    Environment conda@default has been created

- Activate the conda environment::

    [flight@gateway1 ~]$ flight env activate conda
    (base) <conda> [flight@gateway1 ~]$

- Check that conda can be run::

    (base) <conda> [flight@gateway1 ~]$ conda --version
    conda 4.7.10


Installing and Running Perl
---------------------------

An example workflow using perl is demonstrated below.

- View available versions::

    (base) <conda> [flight@gateway1 ~]$ conda search perl
    Loading channels: done
    # Name                       Version           Build  Channel
    perl                          5.26.0      hae598fd_0  pkgs/main
    perl                          5.26.2      h14c3975_0  pkgs/main

- Install specific version::

    (base) <conda> [flight@gateway1 ~]$ conda install perl=5.26.2
    Collecting package metadata (current_repodata.json): done
    Solving environment: done

    ## Package Plan ##

      environment location: /home/flight/.local/share/flight/env/conda+default

      added / updated specs:
        - perl=5.26.2


    The following packages will be downloaded:

        package                    |            build
        ---------------------------|-----------------
        ca-certificates-2019.5.15  |                1         134 KB
        certifi-2019.6.16          |           py37_1         156 KB
        conda-4.7.11               |           py37_0         3.0 MB
        perl-5.26.2                |       h14c3975_0        10.5 MB
        ------------------------------------------------------------
                                               Total:        13.7 MB

    The following NEW packages will be INSTALLED:

      perl               pkgs/main/linux-64::perl-5.26.2-h14c3975_0

    The following packages will be UPDATED:

      ca-certificates                               2019.5.15-0 --> 2019.5.15-1
      certifi                                  2019.6.16-py37_0 --> 2019.6.16-py37_1
      conda                                       4.7.10-py37_0 --> 4.7.11-py37_0


    Proceed ([y]/n)? y


    Downloading and Extracting Packages
    conda-4.7.11         | 3.0 MB    | ############################################################################################ | 100%
    certifi-2019.6.16    | 156 KB    | ############################################################################################ | 100%
    perl-5.26.2          | 10.5 MB   | ############################################################################################ | 100%
    ca-certificates-2019 | 134 KB    | ############################################################################################ | 100%
    Preparing transaction: done
    Verifying transaction: done
    Executing transaction: done

- Check installation location::

    (base) <conda> [flight@gateway1 ~]$ which perl
    ~/.local/share/flight/env/conda+default/bin/perl

- Install perl library (this may prompt for initial ``cpan`` configuration, once configuration is complete then the library will be installed)::

    (base) <conda> [flight@gateway1 ~]$ cpan File::Slurp
    Loading internal null logger. Install Log::Log4perl for logging messages
    Reading '/home/flight/.cpan/Metadata'
      Database was generated on Mon, 09 Sep 2019 15:17:03 GMT
    Running install for module 'File::Slurp'
    <-- snip -->

- Check installation worked::

    (base) <conda> [flight@gateway1 ~]$ cpan File::Slurp
    Loading internal null logger. Install Log::Log4perl for logging messages
    Reading '/home/flight/.cpan/Metadata'
      Database was generated on Mon, 09 Sep 2019 15:17:03 GMT
    File::Slurp is up to date (9999.27).

