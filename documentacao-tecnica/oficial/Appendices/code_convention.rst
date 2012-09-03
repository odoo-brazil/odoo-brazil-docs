Conventions
===========

Guidelines
----------
For guidelines and general recommendations with regard to the development of OpenERP modules,
please refer to the :ref:`Guidelines <contribution_guidelines-link>` of the
:doc:`Contribution section </contribute/index>`.


Module structure and file names
-------------------------------

The structure of a module should be::

    /module/

        /__init__.py
        /__openerp__.py
        /module.py
        /module_other.py
        /module_view.xml
        /module_data.xml
        /module_demo.xml

        /wizard/
        /wizard/__init__.py
        /wizard/wizard_name.py

        /report/
        /report/
        /report/__init__.py
        /report/report_name.sxw
        /report/report_name.rml
        /report/report_name.py

Naming conventions
------------------

    * modules: modules must be written in lower case, with underscores. The name of the module is the name of the directory in the addons path of the server. If the module depends on other modules, you can write several module names separated by underscores, starting by the most important name. Example:
          + sale
          + sale_commission 

    * objects: the name of an object must be of the form name_of_module.name1.name2.name3.... The namei part of the object must go from the most important name to the least important one, from left to right, in lower case. Try not to use plurals in object names and to avoid shortcuts in the names. Example:
          + sale.order
          + sale.order.line
          + sale.shop
          + sale_commission.commission.rate 

    * fields: field must be in lowercase, separated by underscores. Try to use commonly used names for fields: name, state, active, partner_id, eso. Conventions for the field name depends on the field type:
          + many2one: must end by '_id' (eg: partner_id, order_line_id)
          + many2many: must end by '_ids' (eg: category_ids)
          + one2many: must end by '_ids' (eg: line_ids
