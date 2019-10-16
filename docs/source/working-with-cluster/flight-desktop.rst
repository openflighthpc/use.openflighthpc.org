.. _flight-desktop:

Flight Desktop
==============

Your OpenFlight Compute gateway node can run graphical desktop sessions to support users who want to run interactive applications across the cluster. The system can support a number of different sessions simultaneously, and allow multiple remote participants to connect to the same session to support training and collaborative activities.

Install Flight Desktop Environments
-----------------------------------

Your OpenFlight Compute cluster supports many types of graphical session designed to provide interactive applications directly to users. To view the available types of session, use the command ``flight desktop avail``:

.. code:: bash

    [flight@gateway1 (scooby) ~]$ flight desktop avail
    ┌──────────┬───────────────────────────────────────────────────────────────────────────────────────────────────┬────────────┐
    │ Name     │ Summary                                                                                           │ State      │
    ├──────────┼───────────────────────────────────────────────────────────────────────────────────────────────────┼────────────┤
    │ chrome   │ Full-screen Google Chrome browser session.                                                        │ Unverified │
    │          │                                                                                                   │            │
    │          │  > https://www.google.com/chrome/                                                                 │            │
    │          │                                                                                                   │            │
    │ gnome    │ GNOME v3, a free and open-source desktop environment for Unix-like operating systems.             │ Unverified │
    │          │                                                                                                   │            │
    │          │  > https://www.gnome.org/                                                                         │            │
    │          │                                                                                                   │            │
    │ kde      │ KDE Plasma Desktop (KDE 4). Plasma is KDE's desktop environment. Simple by default, powerful when │ Unverified │
    │          │ needed.                                                                                           │            │
    │          │                                                                                                   │            │
    │          │  > https://kde.org/                                                                               │            │
    │          │                                                                                                   │            │
    │ terminal │ Preconfigured terminal for Flight HPC environments.                                               │ Unverified │
    │          │                                                                                                   │            │
    │ xfce     │ Xfce is a lightweight desktop environment for UNIX-like operating systems. It aims to be fast and │ Unverified │
    │          │ low on system resources, while still being visually appealing and user friendly.                  │            │
    │          │                                                                                                   │            │
    │          │  > https://xfce.org/                                                                              │            │
    │          │                                                                                                   │            │
    │ xterm    │ Minimal desktop environment with an xterm terminal window.                                        │ Unverified │
    │          │                                                                                                   │            │
    │          │  > https://invisible-island.net/xterm/xterm.html                                                  │            │
    │          │                                                                                                   │            │
    └──────────┴───────────────────────────────────────────────────────────────────────────────────────────────────┴────────────┘

Application types that are ``unverified`` need to be prepared before they can be started. To prepare a new session type, use the command ``flight desktop prepare <type>`` (preparing will automatically install any required application and support files, if these dependencies have been installed manually then a desktop session can be checked for verfication with ``flight desktop verify <type>``). Once enabled, users can start a new session using the command ``flight desktop start <type>``.

.. note:: The ``prepare`` command is only available to the ``root`` user as it requires installation of packages

.. note:: Preparing a new session type only enables it for the machine that you run the command from, any other nodes will need to have the type enabled too.


Launch a Desktop Session
------------------------

Users can launch a new session by using the ``flight desktop start gnome`` command. After launching the desktop, a message will be pri
nted with connection details to access the new session::

    Starting a 'gnome' desktop session:

       > ✅ Starting session

    A 'gnome' desktop session has been started.

    == Session details ==

      Identity: d33096d5-b50c-49dd-a59e-d5aebc7940ac
          Type: gnome
       Host IP: 52.151.119.86
      Hostname: gateway1
          Port: 5902
       Display: :2
      Password: L9Uysvi3

    This desktop session is not directly accessible from outside of your
    cluster as it is running on a machine that only provides internal
    cluster access.  In order to access your desktop session you will need
    to perform port forwarding using 'ssh'.

    Refer to 'flight desktop show d33096d5' for more details.

    If prompted, you should supply the following password: L9Uysvi3


