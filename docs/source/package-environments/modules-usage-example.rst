.. _modules-usage-example:

Modules: Usage Example
======================


Creating and Using Environment
------------------------------

Flight Env provides quick setup methods to create a modules software environment. 

To install and use modules:

- :ref:`Activate the flight environment <activate-flight-env>`
- Create the modules installation for the user::

    [flight@gateway1 ~]$ flight env create modules
    Creating environment modules@default
       > ✅ Verifying prerequisites
       > ✅ Fetching prerequisite (modules)
       > ✅ Extracting prerequisite (modules)
       > ✅ Building prerequisite (modules)
       > ✅ Installing prerequisite (modules)
       > ✅ Creating environment (modules@default)
    Environment modules@default has been created

- Activate the modules environment::

    [flight@gateway1 ~]$ flight env activate modules
    <modules> [flight@gateway1 ~]$

- Check that modules can be run::

    <modules> [flight@gateway1 ~]$ module --version
    Modules Release 4.3.0 (2019-07-26)


Installing Software
-------------------

Unlike the other :ref:`package environments <package-environments>`, modules provides the environment management tool but not any package management tools. Therefore, with the modules environment, you are free to compile and install software in a module compatible manner.

For more information on building software for modules, see the `modulefile reference <https://modules.readthedocs.io/en/latest/modulefile.html>`_ and build documentation for the chosen software.

