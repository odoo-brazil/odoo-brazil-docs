Data Loading
============

During OpenERP installation, two steps are necessary to create and feed the database:

   1. Create the SQL tables
   2. Insert the different data into the tables 

The creation (or modification in the case of an upgrade) of SQL tables is automated thanks to the description of objects in the server.

Into OpenERP, all the logic of the application is stored in the database. We find for example:

    * the definitions of the reports,
    * the object default values,
    * the form description of the interface client,
    * the relations between the menu and the client buttons, ... 


There must be a mechanism to describe, modify and reload the different data. These data are represented into a set of XML files that can possibly be loaded during start of the program in order to fill in the tables. 
