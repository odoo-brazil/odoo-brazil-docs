Shutting down the server
========================

The easiest way the shut down the server on a Linux system is to send the ``SIG
INT`` signal to the server using the ``kill`` command (or if you are on its
controlling terminal, by pressing ``ctrl-C``). You may need to first run an
additional command to know the process ID (PID) of the server.

    * Find the server PID. ::

          $ ps ax | grep openerp-server

    * Use the ``kill`` command with the server PID. ::

          $ kill -2 <pid>

