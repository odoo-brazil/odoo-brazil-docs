OpenOffice.org reports
======================

**The document flow**


OpenOffice.org reports are the most commonly used report formats. OpenOffice.org Writer is used (in combination with [[1]]) to generate a RML template, which in turn is used to generate a pdf printable report.

.. figure::  images/ooo_report_overview.png
   :scale: 85
   :align: center

**The internal process**

.. figure::  images/process_ooo.png
   :scale: 85
   :align: center

**The .SXW template file**

    * We use a .SXW file for the template, which is the OpenOffice 1.0 format. The template includes expressions in brackets or OpenOffice fields to point where the data from the OpenERP server will be filled in. This document is only used for developers, as a help-tool to easily generate the .RML file. OpenERP does not need this .SXW file to print reports. 

**The .RML template**

    * We generate a .RML file from the .SXW file using Open SXW2RML. A .RML file is a XML format that represent a .PDF document. It can be converted to a .PDF after. We use RML for more easy processing: XML syntax seems to be more common than PDF syntax. 

**The report engine**

    * The Open Report Engine process the .RML file inserting data from the database at each expression. 

in the .RML file will be replaced by the name of the country of the partner of the printed invoice. This report engine produce the same .RML file where all expressions have been replaced by real data.

**The final document**

    * Finally the .RML file is converted to PDF or HTML as needed, using OpenReport's scripts. 

Creating a SXW
--------------

You can design reports using *OpenOffice*. Here, as an example, is the file **server/bin/addons/sale/report/order.sxw**.

.. figure::  images/writer_report.png
   :scale: 85
   :align: center

.. _dynamic-report-content:

Dynamic content in OpenOffice reports 
-------------------------------------

**Dynamic content**

In the .SXW/.RML reports, you can put some Python code that accesses the OpenERP objects in brackets. The context of the code (the variable's values you can use) is the following:

**Available variables**

Here are Python objects/variables available:

    * **objects** : the list of objects to be printed (invoices for example).
    * **data** : comes from the wizard
    * **time** : the Python time module (see Python documentation for more information).
    * **user** : the user object launching the report. 

 **Available functions**

Here are Python functions you can use:

    * **setLang('fr')** : change the language used in automated translation (fields...).
    * **repeatIn(list, varname[, tagname])** : repeat the current part of the template 
      (whole document, current section, current row in the table) for each 
      object in the list. Use varname in the template's tags. Since versions 
      4.1.X, you can use an optional third argument that is the name of the 
      .RML tag you want to loop on.
    * **setTag('para','xpre')** : replace the enclosing RML tag (usually 'para') with an other (xpre is a preformatted paragraph), in the (converted from sxw)rml document (?)
    * **removeParentNode('tr')** : removes the parent node of type 'tr', this parameter is usually used together with a conditional (see examples below)

Example of useful tags:

    * **[[ repeatIn(objects,'o') ]]** : Loop on each objects selected for the print
    * **[[ repeatIn(o.invoice_line,'l') ]]** : Loop on every line
    * **[[ repeatIn(o.invoice_line,'l', 'td') ]]** : Loop on every line and make
      a new table cell for each line.
    * **[[ (o.prop=='draft')and 'YES' or 'NO' ]]** : Print YES or NO according the field 'prop'
    * **[[ round(o.quantity * o.price * 0.9, 2) ]]** : Operations are OK.
    * **[[ '%07d' % int(o.number) ]]** : Number formatting
    * **[[ reduce(lambda x, obj: x+obj.qty , list , 0 ) ]]** : Total qty of list (try "objects" as list)
    * **[[ user.name ]]** : user name
    * **[[ setLang(o.partner_id.lang) ]]** : Localized printings
    * **[[ time.strftime('%d/%m/%Y') ]]** : Show the time in format=dd/MM/YYYY, check python doc for more about "%d", ...
    * **[[ time.strftime(time.ctime()[0:10]) ]]** or **[[ time.strftime(time.ctime()[-4:]) ]]** : Prints only date.
    * **[[ time.ctime() ]]** : Prints the actual date & time
    * **[[ time.ctime().split()[3] ]]** : Prints only time
    * **[[ o.type in ['in_invoice', 'out_invoice'] and 'Invoice' or removeParentNode('tr') ]]** : If the type is 'in_invoice' or 'out_invoice' then the word 'Invoice' is printed, if it's neither the first node above it of type 'tr' will be removed.


One more interesting tag: if you want to print out the creator of an entry 
(create_uid) or the last one who wrote on an entry (write_uid) you have to add 
something like this to the class your report refers to:

.. code-block::python

    'create_uid': fields.many2one('res.users', 'User', readonly=1) 

and then in your report it's like this to print out the corresponding name:

.. code-block::python

    o.create_uid.name 

Sometimes you might want to print out something only if a certain condition is 
met. You can construct it with the python logical operators "not", "and" and 
"or". Because every object in python has a logical value (TRUE or FALSE) you can 
construct something like this:

.. code-block::python

    (o.prop=='draft') and 'YES' or 'NO' #prints YES or NO 

It works like this: `and` is higher priority than `or`, so that expression is
equivalent to this one:

.. code-block::python

    ((o.prop=='draft') and 'YES') or 'NO' 
 
If `o.prop` is `'draft'`, then it evaluates like this:
	#. `o.prop == 'draft'` is `True`.
	#. `True and 'YES'` is `'YES'`. Because the left side is a "true" value, the
	   `and` expression evaluates to the right side.
	#. `'YES' or 'NO'` is `'YES'`. Because the left side is a "true" value, the
	   `or` expression short cuts and ignores the right side. It evaluates to 
	   the left side.

If `o.prop` is something else like `'confirm'`, then it evaluates like this:
	#. `o.prop == 'draft'` is `False`.
	#. `False and 'YES'` is `False`. Because the left side is a "false" value, the
	   `and` expression short cuts and ignores the right side. It evaluates to
	   the left side.
	#. `False or 'NO'` is `'NO'`. Because the left side is a "false" value, the
	   `or` expression evaluates to the right side.

One can use very complex structures. To learn more, see the python manuals
section on `Python's boolean operators`_.


python function "filter" can... filter: try something like:

    repeatIn(filter( lambda l: l.product_id.type=='service' ,o.invoice_line), 'line') 

for printing only product with type='service' in a line's section.

To display binary field image on report (to be checked)

    [[ setTag('para','image',{'width':'100.0','height':'80.0'}) ]] o.image or setTag('image','para') 
 

SXW2RML
-------

Open Report Manual
++++++++++++++++++

About
"""""

The OpenERP's report engine.

Open Report is a module that allows you to render high quality PDF document
from an OpenOffice template (.sxw) and any relational database. It can be used
as an OpenERP module or as a standalone program.

SXW to RML script setup - Windows users
"""""""""""""""""""""""""""""""""""""""

In order to use the 'tiny_sxw2rml.py' Python script you need the following packages installed:

    * Python (http://www.python.org)
    * ReportLab (http://www.reportlab.org)/(Installation)
    * Libxml for Python (http://users.skynet.be/sbi/libxml-python) 

SXW to RML script setup - Linux (Open source) users
"""""""""""""""""""""""""""""""""""""""""""""""""""

The **tiny_sxw2rml.py** can be found in the **base_report_designer** OpenERP module at this location::

  server/bin/addons/base_report_designer/wizard/tiny_sxw2rml/tiny_sxw2rml.py

Ensure normalized_oo2rml.xsl is available to tiny_sxw2rml otherwise you will get an error like:

    * failed to load external entity normalized_oo2rml.xsl 

Running tiny_sxw2rml
""""""""""""""""""""

When you have all that installed just edit your report template and run the script with the following command:
::

  tiny_sxw2rml.py template.sxw > template.rml

Note: **tiny_sxw2rml.py** help suggests that you specify the output file with: "-o OUTPUT" but this does not seem to work as of V0.9.3 

OpenERP Server PDF Output 
--------------------------

Server PDF Output
+++++++++++++++++

About
"""""
To generate the pdf from the rml file, OpenERP needs a rml parser.

Parser
""""""
The parsers are generally put into the report folder of the module. Here is the code for the sale order report:

.. code-block:: python

    import time
    from report import report_sxw


    class order(report_sxw.rml_parse):
        def __init__(self, cr, uid, name, context):
            super(order, self).__init__(cr, uid, name, context)
            self.localcontext.update({
                'time': time,
            })

    report_sxw.report_sxw('report.sale.order', 'sale.order',
          'addons/sale/report/order.rml', parser=order, header=True)


The parser inherit from the **report_sxw.rml_parse** object and it add to the localcontext, the function time so it will be possible to call it in the report.

After an instance of **report_sxw.report_sxw** is created with the parameters:

    * the name of the report
    * the object name on which the report is defined
    * the path to the rml file
    * the parser to use for the report (by default rml_parse)
    * a boolean to add or not the company header on the report (default True) 

The xml definition
""""""""""""""""""

To be visible from the client, the report must be declared in an xml file (generally: "module_name"_report.xml) that must be put in the **__terp__.py** file

Here is an example for the sale order report:
::

	<?xml version="1.0"?>
	<openerp>
		<data>
			<report
	   			id="report_sale_order"
	   			string="Print Order"
	   			model="sale.order"
	   			name="sale.order"
	   			rml="sale/report/order.rml"
	   			auto="False"/>
	   			header="False"/>
	 	</data>
	</openerp>

The arguments are:

    * **id**: the id of the report like any xml tag in OpenERP
    * **string**: the string that will be display on the Client button
    * **model**: the object on which the report will run
    * **name**: the name of the report without the first "report."
    * **rml**: the path to the rml file
    * **auto**: boolean to specify if the server must generate a default parser or not
    * **header**: allows to enable or disable the report header. To edit them for a specific company, go to: Administration -> Users -> Company's structure -> Companies. There, select and edit your company: the "Header/Footer" tab allows you to edit corporate header/footer.  

.. _Python's boolean operators: http://docs.python.org/library/stdtypes.html#boolean-operations-and-or-not
