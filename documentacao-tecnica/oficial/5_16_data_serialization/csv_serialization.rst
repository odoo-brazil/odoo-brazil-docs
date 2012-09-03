
.. _csv_serialization:

CSV Data Serialization
----------------------

Since version 4.2, OpenERP provides a Comma-Separated-Values (CSV),
spreadsheet-compatible data serialization format.

The basic format of an OpenERP CSV file is as follows::

    "id","name","model_id:id","group_id:id","perm_read","perm_write","perm_create","perm_unlink"
    "access_product_uom_categ_manager","product.uom.categ manager","model_product_uom_categ","product.group_product_manager",1,1,1,1
    "access_product_uom_manager","product.uom manager","model_product_uom","product.group_product_manager",1,1,1,1
    "access_product_ul_manager","product.ul manager","model_product_ul","product.group_product_manager",1,1,1,1
    "access_product_category_manager","product.category manager","model_product_category","product.group_product_manager",1,1,1,1
    "access_product_template_manager","product.template manager","model_product_template","product.group_product_manager",1,1,1,1
    "access_product_product_manager","product.product manager","model_product_product","product.group_product_manager",1,1,1,1
    "access_product_packaging_manager","product.packaging manager","model_product_packaging","product.group_product_manager",1,1,1,1
    "access_product_uom_categ_user","product.uom.categ.user","model_product_uom_categ","base.group_user",1,0,0,0
    "access_product_uom_user","product.uom.user","model_product_uom","base.group_user",1,0,0,0
    "access_product_ul_user","product.ul.user","model_product_ul","base.group_user",1,0,0,0
    "access_product_category_user","product.category.user","model_product_category","base.group_user",1,0,0,0
    "access_product_template_user","product.template.user","model_product_template","base.group_user",1,0,0,0
    "access_product_product_user","product.product.user","model_product_product","base.group_user",1,0,0,0
    "access_product_packaging_user","product.packaging.user","model_product_packaging","base.group_user",1,0,0,0


Importing from a CSV
++++++++++++++++++++

Instead of using .XML file, you can import .CSV files. It is simpler but the migration system does not migrate the data imported from the .CSV files. It's like the noupdate attribute in .XML files.
It's also more difficult to keep track of relations between resources and it is slower at the installation of the server.

Use this only for [demo] data that will never been upgraded from one version of OpenERP to another.

The name of the object is the name of the CSV file before the first '-'.
You must use one file per object to import. For example, to import a file with partners (including their
multiple contacts and events), the file must be named like one of the following example:

    * res.partner.csv
    * res.partner-tiny_demo.csv
    * res.partner-tiny.demo.csv

Structure of the CSV file
+++++++++++++++++++++++++

    * Separator to use: ``,``
    * Quote character for strings: ``"`` (optional if no separator is found in field values)
    * Encoding to use: ``UTF-8``
    * No whitespace allowed around separators if not using quote characters
    * Be sure to configure your CSV export software (e.g. spreadsheet editor) with the above parameters

Exporting demo data and import it from a module
+++++++++++++++++++++++++++++++++++++++++++++++

You can import .CSV file that have been exported from the OpenERP client.
This is interesting to create your own demo module. But both formats are not exactly the same,
mainly due to the conversion: Structured Data -> Flat Data -> Structured Data.

    *  .. compound::

          The name of the column (first line of the .CSV file) use the end user term in his own language when
          you export from the client. If you want to import from a module, you must convert the first column
          using the fields names. 
          Example, from the partner form::

              Name,Code,Contacts/Contact Name,Contacts/Street,Contacts/Zip

          becomes::

              name,ref,address/name,address/street,address/zip

    * When you export from the OpenERP client, you can select any many2one fields and their child's relation.
      When you import from a module, OpenERP tries to recreate the relations between the two resources.
      For example, do not export something like this from a sale order form - otherwise OpenERP will not be
      able to import your file::

          Order Description,Partner/Name,Partner/Payable,Partner/Address/Name

    * To find the link for a many2one or many2many field, the server uses the name_search function when importing.
      So, for a many2one field, it is better to export the field 'name' or 'code' of the related resource only.
      Use the more unique one. Be sure that the field you export is searchable by the name_search function.
      (the 'name' column is always searchable)::

          Order Description,Partner/Code

    * Change the title of the column for all many2many or many2one fields. It's because you export the related
      resource and you import a link on the resource.
      Example from a sale order: Partner/Code should become partner_id and not partner_id/code.
      If you kept the ``/code``, OpenERP will try to create those entries in the database instead of finding
      references to existing ones.

    * .. compound::

          Many2many fields. If all the exported data contains 0 or 1 relation on each many2many fields, there will
          be no problem. Otherwise, the export will result in one line per many2many. The import function expects
          to get all many2many relations in one column, separated by a comma.

          So, you have to make the transformation. For example, if the categories "Customer" and "Supplier"
          already exists::

              name,category_id
              Smith, "Customer, Supplier"

          If you want to create these two categories you can try ::

              name,category_id/name
              Smith, "Customer, Supplier"

          But this does not work as expected: a category "Customer, Supplier" is created.
          The solution is to create an empty line with only the second category::

              name,category_id/name
              Smith, Customer
              ,Supplier

          Note the comma before "Supplier"!


    * Read only fields. Do not try to import read only fields like the amount receivable or payable for a partner.
      Otherwise, OpenERP will not accept to import your file.

    * Exporting trees. You can export and import tree structures using the parent field.
      You just have to take care of the import order. The parent have to be created before his child's.

Use record id like in xml file:
+++++++++++++++++++++++++++++++

It's possible to define an id for each line of the csv file. This allow to define references between records:

    id, name, parent_id:id
    record_one, Father,
    record_two, Child, record_one

If you do this, the line with the parent data must be before the child lines in the file.


Multiple CSV Files
------------------

Importing from multiple CSV a full group of linked data
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

It's possible to import a lot of data, with multiple CSV files imported as a single operation. Assume we have a database with books and authors with a relation many2many between book and author.

And that you already have a file with a lot of books (like a library) and an other file with a lot of authors and a third file with the links between them.

How to import that easily in openERP ?

Definition of an import module
++++++++++++++++++++++++++++++

You can do this in the module you have defined to manage yours books and authors. but Sometimes, the tables to import can also be in several modules.

For this example, let's say that 'book' object is defined in a module called 'library_management' and that 'Author' object in a module called 'contact_name'.

In this case, you can create a 'fake' module, just to import the data for all these multiples modules. Call this importation module : 'import_my_books'.

You create this module as others modules of OpenObject :

   1. create a folder 'import_my_books'
   2. inside, create a '__init__.py' file with only one line : import import_my_books
   3. again, in the same folder, create a '__openerp__.py' file and in this file, write the following code :

.. code-block:: python


     # -*- encoding: utf-8 -*-
     {
       'name': 'My Book Import',
       'category': 'Data Module 1',
       'init_xml':[],
       'author': 'mySelf & I',
       'depends': ['base','library_management','contact_name'],
       'version': '1.0',
       'active': False,
       'demo_xml': [],
       'update_xml':['contact_name.author.csv','library.book.csv'],
       'installable': True
     }


Creation of CSV files
+++++++++++++++++++++

For the CSV files, you'll import one after the other.

So you have to choose in which way you'll treat the many2many relation.
For our example, we've choose to import all the authors, then all the books with the links to the authors.

   1. authors CSV file

You have to put your data in a CSV file without any link to books (because the book ids will be known only AFTERWARDS...) For example : ("contact_name.author.csv")

::

     id,last_name,first_name,type
     author_1,Bradley,Marion Zimmer,Book writer
     author_2,"Szu T'su",,Chinese philosopher
     author_3,Zelazny,Roger,Book writer
     author_4,Arleston,Scotch,Screen Writer
     author_5,Magnin,Florence,Comics Drawer
     ...

   1. Books CSV file

Here, you can put the data about your books, but also, the links to the authors, using the same id as the column 'id' of the author CSV file. For example : ("library.book.csv" )

::

     id,title,isbn,pages,date,author_ids:id
     book_a,Les Cours du Chaos,1234567890123,268,1975-12-25,"author_3"
     book_b,"L'art de la Guerre, en 219 volumes",1234567890124,1978-01-01,"author_2"
     book_c,"new marvellous comics",1587459248579,2009-01-01,"author_5,author_4"
     ...

Five remarks :

   1. the field content must be enclosed in double quotes (") if there is a double quote or a comma in the field.
   2. the dates are in the format YYYY-MM-DD
   3. if you have many ids in the same column, you must separate them with a comma, and, by the way, you must enclosed the content of the column between double quotes...
   4. the name of the field is the same as the name of the field in the class definition AND must be followed by ':id' if the content is an ID that must be interpreted by the import module. In fact, "author_4" will be transformed by the import module in an integer id for the database module and this numerical id will be put also in the table between author and book, not the literal ID (author_4).
   5. the encoding to be used by the CSV file is the 'UTF-8' encoding
