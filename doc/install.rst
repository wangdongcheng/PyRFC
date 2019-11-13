.. _installation:

============
Installation
============

Python connector is a wrapper for the *SAP NetWeaver RFC Library* and you need to obtain and install it first.

If Python is not already installed on your system, you need to download and install Python as well.

After having *SAP NW RFC Library* and Python installed on your system, you can download and install one of provided
:mod:`pyrfc` eggs, relevant for your platform and start using :mod:`pyrfc`.

You can also clone this repository and build :mod:`pyrfc` from the source code, following :ref:`build`.

.. _install-c-connector:

SAP NW RFC Library Installation

Windows
-------

1. Create an directory, e.g. ``c:\nwrfcsdk``.
2. Unpack the SAR archive to it, e.g. ``c:\nwrfcsdk\lib`` shall exist.
3. Include the ``lib`` directory to the library search path on Windows, i.e.
   :ref:`extend<install-problems-envvar-win>` the ``PATH`` environment variable.


Linux
-----

1. Create the directory, e.g. ``/usr/sap/nwrfcsdk``.
2. Unpack the SAR archive to it, e.g. ``/usr/sap/nwrfcsdk/lib`` shall exist.
3. Include the ``lib`` directory in the library search path:

   * As ``root``, create a file ``/etc/ld.so.conf.d/nwrfcsdk.conf`` and
     enter the following values:

     .. code-block:: sh

        # include nwrfcsdk
        /usr/sap/nwrfcsdk/lib

   * As ``root``, run the command ``ldconfig``.


.. _install-python-connector:

Python Connector Installation

.. _install-problems:

Problems
========

Behind a Proxy
--------------

If you are within an internal network that accesses the internet through
an HTTP(S) proxy, some of the shell commands will fail with urlopen errors, etc.

Assuming that your HTTP(S) proxy could be accessed via ``http://proxy:8080``, on Windows
you can communicate this proxy to your shell via::

    SET HTTP_PROXY=http://proxy:8080
    SET HTTPS_PROXY=http://proxy:8080

or permanently set environment variables.


SAP NW RFC Library Installation
-------------------------------

1.  ``ImportError: DLL load failed: The specified module could not be found.``

    (Windows)
    This error indicates that the Python connector was not able to find the
    C connector on your system. Please check, if the ``lib`` directory of the
    C connector is in your ``PATH`` environment variable.

2. ``ImportError: DLL load failed: %1 is not a valid Win32 application.``

   (Windows)
   This error occurs when SAP NW RFC Library 64bit version is installed on a system with 32bit version Python.

Environment variables
---------------------

.. _install-problems-envvar-win:

Windows
'''''''
The environment variable may be set within a command prompt via the ``set``
command, e.g.

* ``set PATH=%PATH%;C:\nwrfcsdk\lib`` (extend PATH with the C connector lib)
* ``set HTTPS_PROXY=proxy:8080`` (setting an proxy for HTTPS communication)

When the command prompt is closed, the environment variable is reset. To achieve
a persistent change of the environment variable, do the following (Windows 7):

1. Open the Start Menu and type ``environment`` into the search box.
2. A window opens in which the user variables are displayed in the upper part
   and the system variables in the lower part. You may select and edit
   the desired variable.
3. The modified variables are used when a *new* command prompt is opened.

