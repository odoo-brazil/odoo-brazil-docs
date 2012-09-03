
Deploy
======

This page describes how to deploy a custom version of OpenERP on Windows.

Package script
--------------

The first step is to grab the package script branch::

    bzr branch lp:~openerp-groupes/openerp/package-script

Batch
-----

Go to the *packaging* directory of the branch and copy the file *build.bat* to the *C:\\openerp* directory of your Windows machine.

SSH server
----------

You need to install a SSH server on Windows. You can for example install `freeSSHd <http://www.freesshd.com/>`_.

Fabric
------

You need to install the tool `Fabric <http://docs.fabfile.org/0.9.3/>`_ to run commands on Windows from Linux using SSH. Refer to your linux package manager to install it.

Configure
+++++++++

Go to the *packaging* directory of the branch and edit the file fabfile.py. Change what need to be changed.

Run
+++

run the command::

    fab -H host -u user server

where:
    * *host* is the Windows host name
    * *user* is the Windows user name
