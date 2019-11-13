<<<<<<< HEAD
# PyRFC - The Python RFC Connector

[![license](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

## Description

The _pyrfc_ Python package provides Python bindings for _SAP NetWeaver RFC Library_,
for a comfortable way of calling ABAP modules from Python and Python modules from ABAP,
via SAP Remote Function Call (RFC) protocol.

## Platforms & Prerequisites

The _pyrfc_ has been initially built with Python 2.6 and wheels are provided for Python 2.7 and 3.6, on 64 bit Linux and Windows platform.

OS X and ARM platforms are currently not supported either, as _SAP NW RFC Library_ is not available for those platforms.

On Windows platforms the Microsoft Visual C++ 2005 Service Pack 1 Redistributable Package (KB973544), or [newer](https://www.microsoft.com/en-us/download/details.aspx?id=48145), must be installed, per [SAP Note 1375494 - SAP system does not start after applying SAP kernel patch](https://launchpad.support.sap.com/#/notes/1375494).

To start using _pyrfc_ you need to obtain _SAP NW RFC Library_ from _SAP Service Marketplace_,
following [these instructions](http://sap.github.io/PyRFC/install.html#install-c-connector). The /dist/ folder of this repository contains egg files (.egg) and wheel files (.whl). Either use _easy_install_ to install the appropriate egg file for your system or use _pip_ to install _pyrfc_ from an appropriate wheel file.

A prerequisite to download is having a **customer or partner account** on _SAP Service Marketplace_ and if you
are SAP employee please check [SAP Note 1037575 - Software download authorizations for SAP employees](https://launchpad.support.sap.com/#/notes/1037575).

_SAP NW RFC Library_ is fully backwards compatible, supporting all NetWeaver systems, from today, down to release R/3 4.0.
You can therefore always use the newest version released on Service Marketplace and connect to older systems as well.

## Usage examples
=======
# SAP NW RFC SDK Client for Python

[![license](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

Asynchronous, non-blocking [SAP NetWeawer RFC SDK](https://support.sap.com/en/products/connectors/nwrfcsdk.html) client bindings for Python.

## Features

- Stateless and stateful connections (multiple function calls in the same ABAP session (same context))
- Sequential and parallel calls, using one or more clients
- Automatic conversion between Python and ABAP datatypes
- Extensive unit tests

## Supported platforms

- Python 3, Python 2 [until 2020](https://pythonclock.org/)

- The _pyrfc_ connector can be [built from source](http://sap.github.io/PyRFC/build.html) on all [platforms supported by SAP NW RFC SDK](https://launchpad.support.sap.com/#/notes/2573790).

- Pre-built _pyrfc_ wheels are provided in respective [releases](https://github.com/SAP/PyRFC/releases), for Python 3 and Python 2 (until 2020), for Windows 10, Ubuntu 16.04 and macOS 10.14 (experimental).

## Prerequisites

### All platforms

SAP NW RFC SDK C++ binaries must be downloaded (SAP partner or customer account required) and locally installed ([installation instructions](http://sap.github.io/PyRFC/install.html#sap-nw-rfc-library-installation)). More information on [SAP NW RFC SDK section on SAP Support Portal](https://support.sap.com/en/product/connectors/nwrfcsdk.html).

SAP NW RFC Library is fully backwards compatible, supporting all NetWeaver systems, from today S4, down to R/3 release 4.6C. Using the latest version is recommended.

### Windows

On Windows platforms the Microsoft Visual C++ 2005 Service Pack 1 Redistributable Package (KB973544), or [newer](https://www.microsoft.com/en-us/download/details.aspx?id=48145), must be installed, per [SAP Note 1375494 - SAP system does not start after applying SAP kernel patch](https://launchpad.support.sap.com/#/notes/1375494).

:exclamation: Due to a [change introduced with Python 3.8 for Windows](https://docs.python.org/3.8/whatsnew/3.8.html#bpo-36085-whatsnew), PATH directories are no longer searched for DLL. The SAP NWRFC SDK lib path is no longer required on PATH, for Python >= 3.8.

### macOS

- The macOS firewall stealth mode must be disabled ([Can't ping a machine - why?](https://discussions.apple.com/thread/2554739)):

```shell
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --setstealthmode off
```

- Remote paths must be set in SAP NWRFC SDK for macOS: [documentation](http://sap.github.io/PyRFC/install.html#macos)

- Build from source requires `uchar.h` file, attached to [SAP OSS Note 2573953](https://launchpad.support.sap.com/#/notes/2573953), to be copied to SAP NW RFC SDK include directory: [documentation](http://sap.github.io/PyRFC/install.html#macos)

## Installation

After the SAP NW RFC SDK [installed](#prerequisites) on your system, download the adequate wheel from the [latest release](https://github.com/SAP/PyRFC/releases/latest) and run pip install:

For PyRFC release 1.9.99, for Python 3.7 on Darwin, run for example:

```shell
wget https://github.com/SAP/PyRFC/releases/download/1.9.99/pyrfc-1.9.99-cp38-cp38-macosx_10_15_x86_64.whl

pip install pyrfc-1.9.97-cp37-cp37m-macosx_10_14_x86_64.whl
```

Alternatively, or if the _pyrfc_ package for your platform not provided, [build the package from source](http://sap.github.io/PyRFC/build.html) on your system and pip install:

```shell
git clone https://github.com/SAP/PyRFC.git
cd PyRFC
python setup.py bdist_wheel
pip install dist/pyrfc-1.9.97-cp37-cp37m-macosx_10_14_x86_64.whl
# set ABAP system parameters in test/pyrfc.cfg
pytest -vv
```

See also the the [pyrfc documentation](http://sap.github.io/PyRFC),
complementing _SAP NW RFC SDK_ [documentation](https://support.sap.com/nwrfcsdk).

## Getting started

**Note:** The package must be [installed](#installation) before use.

### Open Connection
>>>>>>> pr/1

In order to call remote enabled ABAP function module (ABAP RFM), first a connection must be opened.

```python
>>> from pyrfc import Connection
>>> conn = Connection(ashost='10.0.0.1', sysnr='00', client='100', user='me', passwd='secret')
```

<<<<<<< HEAD
Using an open connection, we can invoke remote function calls (RFC).
=======
Connection parameters are documented in **sapnwrfc.ini** file, located in the SAP NWRFC SDK `demo` folder.

### Call ABAP function modules

Using an open connection, remote function modules (RFM) can be invoked. More info in [pyrfc documentation](http://sap.github.io/PyRFC/client.html#client-scenariol).
>>>>>>> pr/1

```python
>>> result = conn.call('STFC_CONNECTION', REQUTEXT=u'Hello SAP!')
>>> print result
{u'ECHOTEXT': u'Hello SAP!',
 u'RESPTEXT': u'SAP R/3 Rel. 702   Sysid: ABC   Date: 20121001   Time: 134524   Logon_Data: 100/ME/E'}
```

Finally, the connection is closed automatically when the instance is deleted by the garbage collector. As this may take some time, we may either call the close() method explicitly or use the connection as a context manager:

```python
>>> with Connection(user='me', ...) as conn:
        conn.call(...)
    # connection automatically closed here
```

<<<<<<< HEAD
Alternatively, connection parameters can be provided as a dictionary,
like in a next example, showing the connection via saprouter.

```python
>>> def get_connection(connmeta):
...     """Get connection"""
...     print 'Connecting ...', connmeta['ashost']
...     return Connection(**connmeta)

>>> from pyrfc import Connection

>>> TEST = {
=======
Alternatively, connection parameters can be provided as a dictionary:

```python
>>> def get_connection(conn_params):
...     """Get connection"""
...     print 'Connecting ...', conn_params['ashost']
...     return Connection(**conn_param)

>>> from pyrfc import Connection

>>> abap_system = {
>>>>>>> pr/1
...    'user'      : 'me',
...    'passwd'    : 'secret',
...    'ashost'    : '10.0.0.1',
...    'saprouter' : '/H/111.22.33.44/S/3299/W/e5ngxs/H/555.66.777.888/H/',
...    'sysnr'     : '00',
...    'client'    : '100',
...    'trace' : '3', #optional, in case you want to trace
...    'lang'      : 'EN'
... }

<<<<<<< HEAD
>>> conn = get_connection(TEST)
=======
>>> conn = get_connection(abap_system)
>>>>>>> pr/1
Connecting ... 10.0.0.1

>>>conn.alive
True
```

<<<<<<< HEAD
## Installation & Documentation

For further details on connection parameters, _pyrfc_ installation and usage,
please refer to [_pyrfc_ documentation](http://sap.github.io/PyRFC),
complementing _SAP NW RFC Library_ [programming guide and documentation](http://service.sap.com/rfc-library)
provided on SAP Service Marketplace.
=======
See also the the [pyrfc documentation](http://sap.github.io/PyRFC),
complementing _SAP NW RFC SDK_ [documentation](https://support.sap.com/nwrfcsdk).

## Known Issues

- Python 2 will not be maintained past 2020

- Unicode path fix required for [build from source](http://sap.github.io/PyRFC/build.html) on macOS

## How to obtain support

If you encounter an issue or have a feature request, you can create a [ticket](https://github.com/SAP/PyRFC/issues).

Check out the SCN Forum (search for "pyrfc") and stackoverflow (use the tag "pyrfc"), to discuss code-related problems and questions.

## License

Copyright (c) 2013 SAP SE or an SAP affiliate company. All rights reserved. This file is licensed under the Apache Software License, v. 2 except as noted otherwise in the [LICENSE](LICENSE) file.
>>>>>>> pr/1
