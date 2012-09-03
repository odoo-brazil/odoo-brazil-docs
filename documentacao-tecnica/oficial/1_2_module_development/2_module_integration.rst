Module Integrations
===================

The are many different modules available for OpenERP and suited for different business models. Nearly all of these are optional (except ModulesAdminBase), making it easy to customize OpenERP to serve specific business needs. All the modules are in a directory named addons/ on the server. You simply need to copy or delete a module directory in order to either install or delete the module on the OpenERP platform.

Some modules depend on other modules. See the file addons/module/__openerp__.py for more information on the dependencies.

Here is an example of __openerp__.py:

.. code-block:: python

	{
	    "name" : "Open TERP Accounting",
	    "version" : "1.0",
	    "author" : "Bob Gates - Not So Tiny",
	    "website" : "http://www.openerp.com/",
	    "category" : "Generic Modules/Others",
	    "depends" : ["base"],
	    "description" : """A
	    Multiline
	    Description
	    """,
	    "init_xml" : ["account_workflow.xml", "account_data.xml", "account_demo.xml"],
	    "demo_xml" : ["account_demo.xml"],
	    "update_xml" : ["account_view.xml", "account_report.xml", "account_wizard.xml"],
	    "active": False,
	    "installable": True
	}

When initializing a module, the files in the init_xml list are evaluated in turn and then the files in the update_xml list are evaluated. When updating a module, only the files from the **update_xml** list are evaluated. 
