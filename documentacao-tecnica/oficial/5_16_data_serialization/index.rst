
.. _data-serialization:


------------------
Data Serialization
------------------

During OpenERP installation, two steps are necessary to create and feed the database:

   1. Create the SQL tables
   2. Insert the different data into the tables

The creation (or modification in the case of an upgrade) of SQL tables is automated thanks to the description of objects in the server.

With OpenERP, everything except the business logic of objects is stored in the database. 
We find for example:

    * the definitions of the reports,
    * the default values for fields,
    * the definition of client interfaces for each document (views),
    * the relationships between menus, buttons and actions
    * etc.


There must be a mechanism to describe, modify and reload these different kinds of data. 
OpenERP data may be specified in CSV, XML or YAML serialization files provided by 
modules, and loaded during module installation/upgrade in order to fill or update the
database tables.


.. toctree::
   :maxdepth: 3

   xml_serialization
   yaml_serialization
   csv_serialization

