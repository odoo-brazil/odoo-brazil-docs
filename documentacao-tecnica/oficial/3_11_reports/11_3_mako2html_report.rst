Html Reports Using Mako Templates
=================================

.. note:: Implemented in trunk only

   	Mako is a template library written in Python. It provides a familiar, non-XML syntax which compiles into Python modules for maximum performance.


Mako Template
-------------

Syntax
""""""

  	A Mako template is parsed from a text stream containing any kind of content, XML, HTML, email text, etc. 
  	
  	The template can further contain Mako-specific directives which represent variable and/or expression substitutions, control structures (i.e. conditionals and loops), server-side comments, full blocks of Python code, as well as various tags that offer additional functionality. All of these constructs compile into real Python code. 
  	
  	This means that you can leverage the full power of Python in almost every aspect of a Mako template.

Expression Substitution
"""""""""""""""""""""""

  	The simplest expression is just a variable substitution. The syntax for this is the ${} construct instead of [[ ]] in rml.

eg::

    this is x: ${x}

  	Above, the string representation of x is applied to the template's output stream where x comes from the localcontext supplied to the template's rendering function.

  	The contents within the ${} tag are evaluated by Python directly.

:Control Structures:

    	In Mako, control structures (i.e. if/else, loops (like while and for), as well as things like try/except) are written using the % marker followed by a regular Python control expression, and are "closed" by using another % marker with the tag "end<name>", where "<name>" is the keyword of the expression:

eg::

	% if x==5:
    	  this is some output
	% endif


Python Blocks
-------------

    	Within <% %>, you're writing a regular block of Python code. While the code can appear with an arbitrary level of preceding whitespace, it has to be consistently formatted with itself. Mako's compiler will adjust the block of Python to be consistent with the surrounding generated Python code.

Useful links:
	http://www.makotemplates.org/docs/

An Overview of Sale Order Example
"""""""""""""""""""""""""""""""""

	For Complete Example of Sale_order please Refer the module sale_report_html from :

            https://code.launchpad.net/~openerp-community/openobject-addons/trunk-addons-community

.. code-block:: html

    ## -*- coding: utf-8 -*-
    <html>
    <head>
	    <%include file="mako_header.html"/>
    </head>
    % for o in objects:
    <body>
     	<table width="100" border="0" cellspacing="0" cellpadding="0">
	     	<tr>
     			<td>
				    <p><small><b>Shipping address :</b></small>
			    </td>
		    </tr>
		    <tr>
			    <td>
				    <small>${ o.partner_id.title or '' } ${ o.partner_id.name }</small>
			    </td>
		    </tr>
		    <tr>
     			<td>
				    <small>${ o.partner_shipping_id.state_id and o.partner_shipping_id.state_id.name or '' } ${ o.partner_shipping_id.country_id and o.partner_shipping_id.country_id.name or '' }</small>
			    </td>
		    </tr>
	    </table>
	    <table>
		       <tr align="left">
			      <th>Description</th>
			      <th>VAT</th>
			      <th>Quantity</th>
			      <th>Unit Price</th>
			      <th>Disc.(%)</th>
			      <th>Price</th>
			    </tr>
		    % for line in o.order_line:
			      <tr>
			      <td>${line.name}</p>
			      <td>${', '.join(map(lambda x: x.name, line.tax_id))}</td>
			      <td>${line.product_uos and line.product_uos_qty or line.product_uom_qty}
			      ${line.product_uos and line.product_uos.name or line.product_uom.name}</td>
			      <td>${line.price_unit}</td>
			      <td>${line.discount or 0.00 }</td>
			      <td>${line.price_subtotal or 0.00 }</td>
			      </tr>
		      % if line['notes']:
			      	<tr>
			      	<td>${line.notes}</td>
			      	</tr>

		      % endif
		      % endfor
	    </table>
    </body>
    % endfor
    <%include file="mako_footer.html"/>
    </html>

You can format the report as you need using HTML.

Report with header and footer
"""""""""""""""""""""""""""""

	To create reports with your company header you need to include <%include file=”mako_header.html”/>
	To create reports with your company footer you need to include <%include file=”mako_footer.html”/>
	These files will bring the header and footer that you have defined for your company in the database.

