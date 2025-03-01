####################
Yubikey Windows Lock
####################

A script to lock your Windows machine once a formerly connected Yubikey
is removed.

Requirements
============
Needs a Python installation and yubikey-manager which can be installed with

.. code-block:: shell

    pip install --user yubikey-manager

Usage
=====

Command Line Options
--------------------

.. code-block::

    usage: yubikey_windows_lock.py [-h] [-s SERIAL] [-w WAIT]

    Lock Windows when Yubikey is removed

    options:
    -h, --help            show this help message and exit
    -s SERIAL, -s SERIAL1 SERIAL2 SERIAL3, --serial SERIAL, --serial SERIAL1 SERIAL2 SERIAL3
                            Limit to yubikey with these serial numbers
    -w WAIT, --wait WAIT  The time (in s) between two checks (default: 2)

Start At Windows Login
----------------------
An easy way to automatically launch the script on Windows login is to use Windows Task Scheduler.
Create a basic task that is executed on logon and as action starts a program.
In the ``Program/Script`` field provide the path to ``pythonw.exe`` of your Python installation.
Typically that is

.. code-block::

    C:\Users\<your_username>\AppData\Local\Programs\Python\<your_python_version>\pythonw.exe

In the ``Add arguments`` field you provide the path to ``yubikey_windows_lock.py`` and optionally the
arguments you want to provide to the script.
So it should look something like

.. code-block::

    C:\Users\<your_username>\<path_to_this_repo>\yubikey_windows_lock.py -w 3 -s <your_yubikey_serial>
