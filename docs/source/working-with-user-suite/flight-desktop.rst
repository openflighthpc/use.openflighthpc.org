.. _flight-desktop:

Flight Desktop
==============

Your OpenFlight Compute gateway node can run graphical desktop sessions to support users who want to run interactive applications across the research environment. The system can support a number of different sessions simultaneously, and allow multiple remote participants to connect to the same session to support training and collaborative activities.

Install Flight Desktop Environments
-----------------------------------

Your OpenFlight Compute research environment supports many types of graphical session designed to provide interactive applications directly to users. To view the available types of session, use the command ``flight desktop avail``:

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
       Host IP: 51.104.217.65
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

Users need a VNC client to connect to the graphical desktop session - for a list of tested clients, see :ref:`clientprereqs`.

Users with Mac clients can use the URL provided in the command output to connect to the session; e.g. from the above example, simply enter ``vnc://flight:L9Uysvi3@52.151.119.86:5902`` into the Safari address bar. Linux and Windows users should enter the IP address and port number shown into their VNC client in the format ``IP:port``. For example - for the output above, Linux and Windows client users would enter ``52.151.119.86:5902`` into their VNC client:

.. image:: vncclient.png
    :alt: VNC client configuration

A one-time randomized password is automatically generated automatically by OpenFlight Compute when a new session is started. Linux and Windows users may be prompted to enter this password when they connect to the desktop session.

Once connected to the graphical desktop, users can use the environment as they would a local Linux machine:

.. image:: vncdesktop.png
    :alt: VNC desktop session

Resizing the desktop to fit your screen
---------------------------------------

Specifying a size with the flight desktop tool
**********************************************

When launching a graphical desktop session using the ``flight desktop`` utility, a session resolution can be specified using the ``--geometry <size>`` option. For example, to launch a ``gnome`` desktop session with a resolution of 1920x1080 pixels, use the command:

.. code:: bash

    [flight@gateway1(scooby) ~]$ flight desktop start --geometry 1920x1080 gnome

By default, your graphical desktop session will launch with a compatibility resolution of 1024x768. Users can resize the desktop to fit their screens using the Linux ``xrandr`` command, run from within the graphical desktop session.

To view the available screen resolutions, start a terminal session on your graphical desktop by navigating to the ``Applications`` menu in the top left-hand corner of the screen, then selecting the ``Terminal`` under the ``System tools`` menu.

.. image:: startingterminal.png
    :alt: Starting a terminal session

The ``xrandr`` command will display a list of available resolutions supported by your desktop:

.. code:: bash

    [flight@gateway1(scooby) ~]$ xrandr
    Screen 0: minimum 32 x 32, current 1024 x 768, maximum 32768 x 32768
    VNC-0 connected primary 1024x768+0+0 0mm x 0mm
       1920x1200     60.00
       1920x1080     60.00
       1600x1200     60.00
       1680x1050     60.00
       1400x1050     60.00
       1360x768      60.00
       1280x1024     60.00
       1280x960      60.00
       1280x800      60.00
       1280x720      60.00
       1024x768      60.00*
       800x600       60.00
       640x480       60.00

To set a new resolution, run the ``xrandr`` command again with the ``-s <resolution>`` argument;

  - e.g. to change to 1280x1024, enter the command ``xrandr -s 1280x1024``

Your graphical desktop session will automatically resize to the new resolution requested. Use your local VNC client application to adjust the compression ratio, colour depth and frame-rate sessions in order to achieve the best user-experience for the desktop session.

Viewing and terminating running sessions
----------------------------------------

Users can view a list of the currently running sessions by using the command ``flight desktop list``. One standard Flight Compute login node supports up to 10 sessions running at the same time.

.. code:: bash

    [flight@gateway1 (scooby) ~]$ flight desktop list
    ┌──────────┬──────────┬───────────┬───────────────┬────────────────┬──────────┬────────┐
    │ Identity │ Type     │ Host name │ IP address    │ Display (Port) │ Password │ State  │
    ├──────────┼──────────┼───────────┼───────────────┼────────────────┼──────────┼────────┤
    │ 6200f57c │ terminal │ gateway1  │ 51.104.217.65 │ :2 (5902)      │ KbnGqk0L │ Active │
    │ 70e75a99 │ chrome   │ gateway1  │ 51.104.217.65 │ :4 (5904)      │ UjlrnN9f │ Active │
    │ 809b9466 │ gnome    │ gateway1  │ 51.104.217.65 │ :1 (5901)      │ uxAMZfB7 │ Active │
    │ a43059c5 │ gnome    │ gateway1  │ 51.104.217.65 │ :3 (5903)      │ Ofd1qVdN │ Active │
    └──────────┴──────────┴───────────┴───────────────┴────────────────┴──────────┴────────┘


To display connection information for an existing session, use the command ``flight desktop show <session-ID>``. This command allows users to review the IP-address, port number and one-time password settings for an existing session.

.. code:: bash

    [flight@gateway1 (scooby) ~]$ flight desktop show 6200f57c

    == Session details ==

      Identity: 6200f57c-ead7-45d5-901d-0b1f9a1d2dad
          Type: terminal
       Host IP: 51.104.217.65
      Hostname: gateway1
          Port: 5902
       Display: :2
      Password: KbnGqk0L

    This desktop session is accessible from the public internet. However,
    please be aware that desktop sessions accessed over the public
    internet are not secure and steps should be taken to secure the link.

    We highly recommend that you access your desktop session using 'ssh'
    port forwarding:

      ssh -L 5901:localhost:5902 flight@51.104.217.65

    Once the ssh connection has been established, depending on your
    client, you can connect to the session using one of:

      vnc://flight:KbnGqk0L@localhost:5901
      localhost:5901
      localhost:1

    If, when connecting, you receive a warning as follows, try again with
    a different port number, e.g. 5902, 5903 etc.:

      channel_setup_fwd_listener_tcpip: cannot listen to port: 5901

    If prompted, you should supply the following password: KbnGqk0L

Users can terminate a running session by ending their graphical application (e.g. by logging out of a Gnome session, or exiting a terminal session), or by using the ``flight desktop kill <session-ID>`` command. A terminated session will be immediately stopped, disconnecting any users.

Securing your graphical desktop session
---------------------------------------

As the VNC protocol does not natively provide support for security protocols such as SSL, you may wish to take steps to secure access to your VNC sessions.

Several third party tools exist to help you secure your VNC connections.  One option is `ssvnc`, available `here <http://www.karlrunge.com/x11vnc/ssvnc.html>`__.

Alternatively, you could use an SSH tunnel to access your session. `Refer to online guides for setup instructions <http://www.cl.cam.ac.uk/research/dtg/attarchive/vnc/sshvnc.html>`_.
