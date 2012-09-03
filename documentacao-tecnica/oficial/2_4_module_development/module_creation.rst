Module creation
===============

Getting the skeleton directory
------------------------------

You can copy __openerp__.py and __init__.py from any other module to create a new module into a new directory.

As an example on Ubuntu:
::

	$ cd ~/workspace/stable/stable_addons_5.0/
	$ mkdir travel
	$ sudo cp ~/workspace/stable/stable_addons_5.0/hr/__openerp__.py ~/workspace/stable/stable_addons_5.0/travel
	sudo cp ~/workspace/stable/stable_addons_5.0/hr/__init__.py ~/workspace/stable/stable_addons_5.0/travel

You will need to give yourself permissions over that new directory if you want
to be able to modify it: ::

    $ sudo chown -R `whoami` travel

You got yourself the directory for a new module there, and a skeleton
structure, but you still need to change a few things inside the module's
definition...

Changing the default definition
-------------------------------

To change the default settings of the "travel" module,
get yourself into the "travel" directory and edit *__openerp__.py* (with *gedit*,
for example, a simple text editor. Feel free to use another one) ::

    $ cd travel
    $ gedit __openerp__.py

The file looks like this:

.. code-block:: python

    {
      "name" : "Human Resources",
      "version" : "1.1",
      "author" : "Tiny",
      "category" : "Generic Modules/Human Resources",
      "website" : "http://www.openerp.com",
      "description": """
      Module for human resource management. You can manage:
      * Employees and hierarchies
      * Work hours sheets
      * Attendances and sign in/out system

      Different reports are also provided, mainly for attendance statistics.
      """,
      'author': 'Tiny',
      'website': 'http://www.openerp.com',
      'depends': ['base', 'process'],
      'init_xml': [],
      'update_xml': [
          'security/hr_security.xml',
          'security/ir.model.access.csv',
          'hr_view.xml',
          'hr_department_view.xml',
          'process/hr_process.xml'
      ],
      'demo_xml': ['hr_demo.xml', 'hr_department_demo.xml'],
      'installable': True,
      'active': False,
      'certificate': '0086710558965',
    }

You will want to change whichever settings you feel right and get something like this:

.. code-block:: python

    {
        "name" : "Travel agency module",
        "version" : "1.1",
        "author" : "Tiny",
        "category" : "Generic Modules/Others",
        "website" : "http://www.openerp.com",
        "description": "A module to manage hotel bookings and a few other useful features.",
        "depends" : ["base"],
        "init_xml" : [],
        "update_xml" : ["travel_view.xml"],
        "active": True,
        "installable": True
    }


Note the "active" field becomes true.

Changing the main module file
-----------------------------

Now you need to update the travel.py script to suit the needs of your module.
We suggest you follow the Flash tutorial for this or download the travel agency
module from the 20 minutes tutorial page.  ::

    The documentation below is overlapping the two next step in this wiki tutorial,
    so just consider them as a help and head towards the next two pages first...

The travel.py file should initially look like this:

.. code-block:: python

    from osv import osv, fields

    class travel_hostel(osv.osv):
           _name = 'travel.hostel'
           _inherit = 'res.partner'
           _columns = {
           'rooms_id': fields.one2many('travel.room', 'hostel_id', 'Rooms'),
           'quality': fields.char('Quality', size=16),
           }
           _defaults = {
           }
    travel_hostel()

Ideally, you would copy that bunch of code several times to create all the
entities you need (travel_airport, travel_room, travel_flight). This is what
will hold the database structure of your objects, but you don't really need to
worry too much about the database side. Just filling this file will create the
system structure for you when you install the module.

Customizing the view
--------------------

You can now move on to editing the views. To do this, edit the custom_view.xml file. It should first look like this:

.. code-block:: xml

    <openerp>
    <data>
        <record model="res.groups" id="group_compta_user">
                <field name="name">grcompta</field>
        </record>
        <record model="res.groups" id="group_compta_admin">
                <field name="name">grcomptaadmin</field>
        </record>
        <menuitem name="Administration" groups="admin,grcomptaadmin"
		        icon="terp-stock" id="menu_admin_compta"/>
    </data>
    </openerp>

This is, as you can see, an example taken from an accounting system (French
people call accounting "comptabilité", which explains the compta bit).

Defining a view is defining the interfaces the user will get when accessing
your module. Just defining a bunch of fields here should already get you
started on a complete interface. However, due to the complexity of doing it
right, we recommend, once again, that download the travel agency module example from this link http://www.openerp.com/download/modules/5.0/.

Next you should be able to create different views using other files to separate
them from your basic/admin view.

