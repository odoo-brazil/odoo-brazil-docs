OpenERP Module Descriptor File : __openerp__.py
===============================================

Normal Module
-------------

In the created module directory, you must add a **__openerp__.py** file. This file, which must be in Python format, is responsible to

   1. determine the XML files that will be parsed during the initialization of the server, and also to
   2. determine the dependencies of the created module.

This file must contain a Python dictionary with the following values:

**name**

    The (Plain English) name of the module.

**version**

    The version of the module.

**description**

    The module description (text).

**author**

    The author of the module.

**website**

    The website of the module.

**license**

    The license of the module (default:GPL-2).

**depends**

    List of modules on which this module depends. The base module must almost always be in the dependencies because some necessary data for the views, reports, ... are in the base module.

**init_xml**

    List of .xml files to load when the server is launched with the "--init=module" argument. Filepaths must be relative to the directory where the module is. OpenERP XML File Format is detailed in this section.

**update_xml**

    List of .xml files to load when the server is launched with the "--update=module" launched. Filepaths must be relative to the directory where the module is. OpenERP XML File Format is detailed in this section.

**installable**

    True or False. Determines if the module is installable or not.

**active**

    True or False (default: False). Determines the modules that are installed on the database creation.

Example
+++++++

Here is an example of __openerp__.py file for the *product* module:

.. code-block:: python

    {
        "name" : "Products & Pricelists",
        "version" : "1.1",
        "author" : "Open",
        "category" : "Generic Modules/Inventory Control",
        "depends" : ["base", "account"],
        "init_xml" : [],
        "demo_xml" : ["product_demo.xml"],
        "update_xml" : ["product_data.xml","product_report.xml", "product_wizard.xml","product_view.xml", "pricelist_view.xml"],
        "installable": True,
        "active": True
    }

The files that must be placed in init_xml are the ones that relate to the workflow definition, data to load at the installation of the software and the data for the demonstrations.

The files in **update_xml** concern: views, reports and wizards.

Profile Module
--------------

The purpose of a profile is to initialize OpenERP with a set of modules directly after the database has been created. A profile is a special kind of module that contains no code, only *dependencies on other modules*.

In order to create a profile, you only have to create a new directory in server/addons (you *should* call this folder profile_modulename), in which you put an *empty* __init__.py file (as every directory Python imports must contain an __init__.py file), and a __openerp__.py whose structure is as follows :

.. code-block:: python

    {
         "name":"''Name of the Profile'',
         "version":"''Version String''",
         "author":"''Author Name''",
         "category":"Profile",
         "depends":[''List of the modules to install with the profile''],
         "demo_xml":[],
         "update_xml":[],
         "active":False,
         "installable":True,
    }

Example
+++++++

Here's the code of the file
server/bin/addons/profile_manufacturing/__openerp__.py, which corresponds to the
manufacturing industry profile in OpenERP.

.. code-block:: python

    {
         "name":"Manufacturing industry profile",
         "version":"1.1",
         "author":"Open",
         "category":"Profile",
         "depends":["mrp", "crm", "sale", "delivery"],
         "demo_xml":[],
         "update_xml":[],
         "active":False,
         "installable":True,
    }

