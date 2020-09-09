.. _flight-job:

Flight Job
==========

The Flight User Suite comes with a utility to jumpstart running jobs on the research environment. This tool provides preconfigured script templates. 

Showing Available Job Scripts
-----------------------------

To show the available guides, list them with::

    [flight@gateway1 (scooby) ~]$ flight job list
    ┌───────┬─────────────────┐
    │ Index │ Name            │
    ├───────┼─────────────────┤
    │ 1     │ mpi-nodes.sh    │
    │ 2     │ mpi-slots.sh    │
    │ 3     │ simple.sh       │
    │ 4     │ simple-array.sh │
    │ 5     │ smp.sh          │
    └───────┴─────────────────┘


Viewing Script Information
--------------------------

The various job scripts have descriptions that explain the purpose of the template. 

To view the description of a job script::

    [flight@gateway1 (scooby) ~]$ flight job info 1
    mpi-nodes.sh - MPI multiple node (Slurm)

      DESCRIPTION

      Submit a single job that spans multiple nodes where you want exclusive use of each node allocated.

      LICENSE

      This work is licensed under a Creative Commons Attribution-ShareAlike 4.0 International License.

      COPYRIGHT

      Copyright (C) 2020 Alces Flight Ltd.

.. note:: The script can be referred to by its name or index

Copying Job Script
------------------

The job utility provides helpers to create copies of the various scripts. To copy a script to the current directory::

    [flight@gateway1 (scooby) ~]$ flight job cp 2
    Successfully copied the template to: /home/flight/mpi-slots.sh

.. note:: The script can be referred to by its name or index

Further control over the copying & naming of the file, following the cp command with a path/name will copy the script as such::

    [flight@gateway1 (scooby) ~]$ flight job cp 4 myjob/run.sh
    Successfully copied the template to: /home/flight/myjob/run.sh

.. note:: If the output directory doesn't exist then ``flight job`` will attempt to create it

