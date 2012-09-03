

.. warning:: This section needs to be rewritten or improved. If you think you
             can contribute to this effort, and are already familiar with Launchpad 
             and OpenERP's source control system, Bazaar, please have a look at:

                 * the section explaining how you can download and build the
                   current documentation on your system: :ref:`building_documentation`
                 * an RST primer such as `this one <http://sphinx.pocoo.org/rest.html>`_ to learn 
                   how you can start modifying the documentation content

.. _technical_update_procedure:

=========================
Upgrading Server, Modules 
=========================

The upgrade from version to version is automatic and doesn't need any special
scripting on the user's part. In fact, the server is able to automatically
rebuild the database and the data from a previously installed version.

The tables are rebuilt from the current module definitions. To rebuild the
tables, the server uses the definition of the objects and adds / modifies
database fields as necessary.

To invoke a database upgrade after installing a new version, you need to start
the server with the **--update=all** argument :

::

	openerp-server.py --update=all

You can also only upgrade specific modules, for example:

::

	openerp-server.py --update=account,base

The database is rebuilt according to information provided in XML files and
Python Classes.
You can also execute the server with **--init=all**. The server will then
rebuild the database according to the existing XML files on the system, delete
all existing data and return OpenERP to its basic configuration.



Detailed update operations
++++++++++++++++++++++++++

OpenERP has a built-in migration and upgrade system which allows updates to be nearly (or often) automatic.
This system also allows to easily include custom modules.

Table/Object structure
""""""""""""""""""""""

When you run openerp-server with option ``--init`` or ``--update``, the table 
structure is updated to match the new description that is in Python code. Fields 
that are removed from Python code are not removed from the postgresql database 
to avoid losing data.

So, simply running with ``--update`` or ``--init``, will upgrade your table structure.

It's important to run ``--init=module`` the first time you install the module. 
Next time, you must use the ``--update=module`` argument instead of the init 
one. This is because ``--init`` loads resources that are loaded only once and 
never upgraded (i.e., resources with no ``id=""`` attribute or within a 
``<data noupdate="1">`` tag). The ``noupdate`` attribute can be overridden by
marking a record with ``forcecreate="True"``. This means that the record will be
created if it doesn't already exist in the database, but it won't be modified.

Data
""""
Some data is automatically loaded at the installation of OpenERP:

    * views, actions, menus,
    * workflows,
    * demo data

This data is also migrated to a new version if you run --update or --init.

Workflows
"""""""""

Workflows are also upgraded automatically. If some activities are removed, the documents states evolves automatically to the preceding activities. That ensure that all documents are always in valid states.

You can freely remove activities in your XML files. If workitems are in this activity, they will evolve to the preceding unlinked activity. And after the activity will be removed.

Things to care about during development
"""""""""""""""""""""""""""""""""""""""

Since version 3.0.2 of OpenERP, you can not use twice the same 'id="..."' during resource creation in your XML files, unless they are in two different modules.

Resources which don't contain an id are created (and updated) only once; at the installation of the module or when you use the --init argument.

If a resource has an id and this resource is not present anymore in the next version of the XML file, OpenERP will automatically remove it from the database. If this resource is still present, OpenERP will update the modifications to this resource.

If you use a new id, the resource will be automatically created at the next update of this module.

**Use explicit id declaration !**, Example:

    * view_invoice_form,
    * view_move_line_tree,
    * action_invoice_form_open, ...

It is important to put id="...." to all record that are important for the next version migrations. For example, do not forget to put some id="..." on all workflows transitions. This will allows OpenERP to know which transition has been removed and which transition is new or updated.

Custom modules
""""""""""""""

For example, if you want to override the view of an object named 'invoice_form' in your xml file (id="invoice_form"). All you have to do is redefine this view in your custom module with the same id. You can prefix ids with the name of the module to reference an id defined in another module.

Example:

    <record model="ir.ui.view" id="account.invoice_form">
    ...
    <record>

This will override the invoice form view. You do not have to delete the old view, like in 3.0 versions of OpenERP.

Note that it is often better to use view inheritance instead of overwriting views.

In this migration system, you do not have to delete any resource. The migration system will detect if it is an update or a delete using id="..." attributes. This is important to preserve references during migrations.

Demo data
""""""""""

Demo data does not have to be upgraded; because it was probably modified or 
deleted by users. To avoid demo data being upgraded you can put a 
``noupdate="1"`` attribute in the ``<data>`` tag of your .xml data files.

Summary of update and init process
++++++++++++++++++++++++++++++++++

init:

    modify/add/delete demo data and built-in data

update:

    modify/add/delete non demo data

Examples of built-in (non demo) data:

    * Menu structure,
    * View definition,
    * Workflow description, ...
    * Everything that has an `id` attribute in the XML data declaration (if no attr noupdate="1" in the header)

What's going on during the update process:

   1. If you manually added data within the client:
          * the update process will not change them
   2. If you dropped data:
          * if it was demo data, the update process will do nothing
          * if it was built-in data (like a view), the update process will recreate it
   3. If you modified data (either in the .XML or the client):
          * if it's demo data: nothing
          * if it's built-in data, data are updated
   4. If built-in data have been deleted in the .XML file:
          * this data will be deleted in the database.
