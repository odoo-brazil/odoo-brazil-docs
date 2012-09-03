Working with Web Services
=========================

Given the architecture of OpenERP, it is not possible to reliably access the
database with the PostgreSQL client or through a direct connection method
such as ODBC.
Fortunately, OpenERP provides a very comprehensive set of web services that
allow you to do everything through standard protocols.

.. note::
   Though it is technically possible, you must be aware that this can have
   disastrous consequences for your data, unless you know exactly what you are
   doing. You are advised to shut down the OpenERP server when accessing the
   database to avoid caching and concurrency issues.

Supported Web Services Protocols
--------------------------------
The currently supported protocols are XML-RPC and Net-RPC. XML-RPC is one of the
first standard for web services, and can be used in almost any language.
It is a pretty verbose protocol, which may sometimes introduce a bit of latency.
Net-RPC, on the other hand, is an optimized protocol particularly designed for
use between applications written in Python.

Support for REST-style webservices is planned for future releases of OpenERP.

Support for the SOAP protocol is deprecated at the moment, but could maybe be
revived if sufficient interest is found in the community.

Available Web Services
----------------------
The OpenERP server provides you with the following web services.

.. note::
    You may find out the details of each service in the corresponding class
    in the server sources, in bin/service/web_services.py .

:db:
    Provides functions to create, drop, backup and restore databases.
    Use with caution!

:common:
    Lets you log in and out of OpenERP, and provides various utility functions. You
    will need to call the function "login" before you can use most of the other
    web services.

:object:
    The most useful web service, as it provides access to the OpenERP Objects.
    Most notably, the function "execute" lets you call methods of the Objects, such
    as moste of the ORM methods to search, read and write records. It can also be
    used to call any other method of the object, such as computing a price for
    example.

.. note::
    Here is a quick reminder of the main ORM methods:
    
    create({'field':'value'})
          * Creates a new record with the specified value
          * Returns: id of the new record
    
    search([('arg1','=','value1')...], offset=0, limit=1000)
          * arg1, arg2, .. ,argN: list of tuples specifying search criteria
          *	offset: optional number of records to skip
          * limit: optional max number of records to return
          * Returns: list of IDS of records matching the given criteria 
    
    read([IDS], ['field1','field2',...])
          * fields: optional list of field names to return (default: all fields)
          * Returns: the id of each record and the values of the requested field
      
    write([IDS], {'field1':'value1','field2':3})
          * values: dictionary of field values to update
          * Updates records with given ids with the given values
          * Returns: True
    
    unlink([IDS])
          * Deletes records with the given ids
          * Returns: True
          
    browse() can't be used through web services.

Another useful function is "exec_workflow", which lets you make a record
progress through a workflow.

:wizard:

Provides access to the old-style wizards. Please note that the new-style wizards
are based on the ORM, and as such they can be accessed though the "object" web
service.

:report:

Lets you generate and retrieve reports.

Example : writing data through the Web Services
-----------------------------------------------

Here is an example process that you could follow to write data. You will find
more detailed examples for XML-RPC in various programming languages in the next
chapter.

#.  login: call "login" in the web service "common" with the following
    parameters:

        * database
        * user name
        * password

#.  create a new partner: call "execute" in the web service "object" with the
    following parameters:

        * database
        * user id provided by "login" in step 1.
        * the object name : 'res.partner'
        * the name of the ORM method : "create"
        * some data to be recorded

The data mentioned above is a dictionary of keys and values, for example:

    * name: Fabien Pinckaers
    * lang: fr_FR

But more complex data structures can also be sent - for example you could record
a partner and his addresses, all in a single call to the web service.
In that case, all the data is processed by the server during the same
database transaction - meaning you are sure to keep a consistent state for
your data - a critical requirement for all ERP applications.
