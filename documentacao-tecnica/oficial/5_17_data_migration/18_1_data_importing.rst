Data Importation
================

Introduction
------------

There are different methods to import your data into OpenERP:

* Through the web-service interface
* Using CSV files through the client interface
* Building a module with .XML or .CSV files with the content
* Directly into the SQL database, using an ETL


Importing data through a module
-------------------------------

The best way to import data in OpenERP is to build a module that
integrates all the data you want to import. So, when you want to
import all the data, you just have to install the module and OpenERP
manages the different creation operations. When you have lots of different
data to import, we sometimes create different modules.

So, let's create a new module where we will store all our data. To do
this, from the addons directory, create a new module called data_yourcompany.

* mkdir data_yourcompany
* cd data_yourcompany
* touch __init__.py

You must also create a file called __openerp__.py in this new module.
Write the following content in this module file description.

.. code-block:: python

  {
    'name': 'Module for Data Importation',
    'version': '1.0',
    'category': 'Generic Modules/Others',
    'description': "Sample module for data importation.",
    'author': 'Tiny',
    'website': 'http://www.openerp.com',
    'depends': ['base'],
    'init_xml': [
        'res.partner.csv',
        'res.partner.address.csv'
    ],
    'update_xml': [],
    'installable': True,
    'active': False,
  }

The following module will import two different files:

* res.partner.csv : a CSV file containing records of the res.partner object
* res.partner.address.csv : a CSV file containing records of the res.partner.address object

Once this module is created, you must load data from your old application to
.CSV file that will be loaded in OpenERP. OpenERP has a builtin system to
manage identifications columns of the original software.

For this exercise, we will load data from another OpenERP database called old.
As this database is in SQL, it's quite easy to export the data using the command
line postgresql client: psql. As to get a result that looks like a .CSV file,
we will use the following arguments of psql:

* -A : display records without space for the row separators
* -F , : set the separator character as ','
* --pset footer : don't write the latest line that looks like "(21 rows)"

When you import a .CSV file in OpenERP, you can provide a 'id' column that
contains a uniq identification number or string for the record. We will use
this 'id' column to refer to the ID of the record in the original application.
As to refer to this record from a many2one field, you can use 'FIELD_NAME:id'.
OpenERP will re-create the relationship between the record using this uniq
ID.

So let's start to export the partners from our database using psql: ::
::

	  psql trunk -c "select 'partner_'||id as id,name from res_partner" 
	             -A -F , --pset footer > res.partner.csv

This creates a res.partner.csv file containing a structure that looks like this:

::

	  id,name
	  partner_2,ASUStek
	  partner_3,Agrolait
	  partner_4,Camptocamp
	  partner_5,Syleam

By doing this, we generated data from the res.partner object, by creating a uniq
identification string for each record, which is related to the old application's
ID.

Now, we will export the table with addresses (or contacts) that are linked to
partners through the relation field: partner_id. We will proceed in the same
way to export the data and put them into our module:

::

  psql trunk -c "select 'partner_address'||id as id,name,'partner_'||
                partner_id as \"partner_id:id\" from res_partner_address" 
                -A -F , --pset footer > res.partner.address.csv

This should create a file called res.partner.address with the following data:

::

  id,name,partner_id:id
  partner_address2,Benoit Mortier,partner_2
  partner_address3,Laurent Jacot,partner_3
  partner_address4,Laith Jubair,partner_4
  partner_address5,Fabien Pinckaers,partner_4

When you will install this module, OpenERP will automatically import the partners
and then the address and recreate efficiently the link between the two records.
When installing a module, OpenERP will test and apply the constraints for consistency
of the data. So, when you install this module, it may crash, for example, because
you may have different partners with the same name in the system. (due to the uniq
constraint on the name of a partner). So, you have to clean your data before importing
them.

If you plan to upload thousands of records through this technique, you should consider
using the argument '-P' when running the server.

::

  openerp_server.py -P status.pickle --init=data_yourcompany

This method provides a faster importation of the data and, if it crashes in the middle
of the import, it will continue at the same line after rerunning the server. This may
preserves hours of testing when importing big files.

Using OpenERP's ETL
--------------------

The next version of OpenERP will include an ETL module to allow you
to easily manages complex import jobs. If you are interested in this
system, you can check the complete specifications and the available
prototype at this location:

  bzr branch lp:~openerp-commiter/openobject-addons/trunk-extra-addons/etl

... to be continued ...

