
OpenERP Server and Web Client - Start/Stop
==========================================

OpenERP 4.2
-----------

First check that all the required dependencies are installed. Then create the terp database. You have to make sure that your user has the correct credentials to create databases with PostgreSQL. For more information on this subject please refer to the PostgreSQL manual.::

	$ createdb terp --encoding=unicode

Once the database created, you can start OpenERP. The content of the database will automatically be created at the first start.::

	$ ./tinyerp-server.py

OpenERP 5.0 and above
---------------------

    * Check that all the required dependencies are installed.
    * Make sure you are logged on as a user that has catalog admin rights in PostgreSQL. Refer to the PostgreSQL manual for more info on this.
    * Start the OpenERP Server 

::

	./openerp-server.py

    * Finally connect to the server with the GTK Client or eTiny and use the Create Database option to create your database 


