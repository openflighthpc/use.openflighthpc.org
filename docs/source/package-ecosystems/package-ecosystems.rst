.. _package-ecosystems:

Package Ecosystems
==================

The Flight Env command provides streamlined installation of many popular software management ecosystems. These can be seen below along with the features they provide.

.. tabularcolumns:: |C|C|C|C|C|C|C|

+---------------+-------+-----------+----------+---------+-------------+-------+
|               | conda | easybuild | gridware | modules | singularity | spack |
|               |       |           |          |         |             |       |
+===============+=======+===========+==========+=========+=============+=======+
| Dependency    | ``y`` |   ``y``   |  ``y``   |  ``n``  |   ``y``     | ``y`` |
| Management    |       |           |          |         |             |       |
+---------------+-------+-----------+----------+---------+-------------+-------+
| Compilation   | ``y`` |   ``y``   |  ``n``   |  ``n``  |   ``n``     | ``y`` |
+---------------+-------+-----------+----------+---------+-------------+-------+
| Preconfigured | ``n`` |   ``y``   |  ``y``   |  ``n``  |   ``y``     | ``*`` |
| Binaries      |       |           |          |         |             |       |
+---------------+-------+-----------+----------+---------+-------------+-------+
| Multiple      | ``*`` |   ``y``   |  ``y``   |  ``y``  |   ``y``     | ``y`` |
| Versions      |       |           |          |         |             |       |
+---------------+-------+-----------+----------+---------+-------------+-------+

More information on the features:

  - **Dependency Management** - The ecosystem automatically resolves and installs dependencies
  - **Compilation** - The ecosystem builds software from source for optimised functionality on the system (Note: these sorts of installations will take a long time)
  - **Preconfigured Binaries** - The ecosystem provides binaries of the available software for quicker installation to get applications installed quickly
  - **Multiple Versions** - The ecosystem allows for installation of multiple versions of software which can be toggled between

``*`` is for partial support. Technically these features are supported in certain use cases and with additional work. This is not considered full support as multiple versions may require undocumented or uncommon use-cases of the tool. 


`Conda <https://conda.io/>`_
----------------------------

Conda is an open source package management system and environment management system that runs on Windows, macOS and Linux. Conda quickly installs, runs and updates packages and their dependencies. Conda easily creates, saves, loads and switches between environments on your local computer. It was created for Python programs, but it can package and distribute software for any language.

`Easybuild <https://easybuilders.github.io/easybuild/>`_
--------------------------------------------------------

EasyBuild is a software build and installation framework that allows you to manage (scientific) software on High Performance Computing (HPC) systems in an efficient way.

`Gridware <https://gridware.alces-flight.com/>`_
------------------------------------------------

Gridware provides pre-compiled binaries for many different scientific computing programs which can be installed quickly and loaded into the environment via modules.

`Modules <http://modules.sourceforge.net/>`_
--------------------------------------------

Modules provides simple environment management. Tools and software to be used with modules will be compiled or installed outside of the modules environment.


`Singularity <https://www.sylabs.io/>`_
---------------------------------------

Singularity is high-performance container technology specifically designed to enhance Enterprise Performance Computing by building containers that support HPC, analytics, artificial intelligence, machine learning, and deep learning to provide “intelligence anywhere.”

`Spack <https://spack.io/>`_
----------------------------

Spack is a package manager for supercomputers, Linux, and macOS. It makes installing scientific software easy. With Spack, you can build a package with multiple versions, configurations, platforms, and compilers, and all of these builds can coexist on the same machine.

