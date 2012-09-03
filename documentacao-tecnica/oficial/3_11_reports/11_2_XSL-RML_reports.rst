XSL:RML reports
===============

RML reports don't require programming but require two simple XML files to be written:

    * a file describing the data to export (\*.xml)
    * a file containing the presentation rules to apply to that data (\*.xsl)

.. figure::  images/automatic-reports.png
   :scale: 85
   :align: center

The role of the XML template is to describe which fields of the resource have to be exported (by the server). The XSL:RML style sheet deals with the layout of the exported data as well as the "static text" of reports. Static text is referring to the text which is common to all reports of the same type (for example, the title of table columns).

**Example**

Here is, as an example, the different files for the simplest report in the ERP.


.. figure::  images/ids-report.png
   :scale: 85
   :align: center


**XML Template**
::

	<?xml version="1.0"?>

	    <ids> 
	    <id type="fields" name="id">

		<name type="field" name="name"/> 
		<ref type="field" name="ref"/> 

	    </id> 
	    </ids> 

**XML data file (generated)**
::

	<?xml version="1.0"?>

	    <ids> 
	    <id>

		<name>Tiny sprl</name> 
		<ref>pnk00</ref> 

	    </id><id>

		<name>ASUS</name> 
		<ref></ref> 

	    </id><id>

		<name>Agrolait</name> 
		<ref></ref> 

	    </id><id>

		<name>Banque Plein-Aux-As</name> 
		<ref></ref> 

	    </id><id>

		<name>China Export</name> 
		<ref></ref> 

	    </id><id>

		<name>Ditrib PC</name> 
		<ref></ref> 

	    </id><id>

		<name>Ecole de Commerce de Liege</name> 
		<ref></ref> 

	    </id><id>

		<name>Elec Import</name> 
		<ref></ref> 

	    </id><id>

		<name>Maxtor</name> 
		<ref></ref> 

	    </id><id>

		<name>Mediapole SPRL</name> 
		<ref></ref> 

	    </id><id>

		<name>Opensides sprl</name> 
		<ref>os</ref> 

	    </id><id>

		<name>Tecsas sarl</name> 
		<ref></ref> 

	    </id> 
	    </ids> 


**XSL stylesheet**
::

	<?xml version="1.0" encoding="utf-8"?> <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:fo="http://www.w3.org/1999/XSL/Format">

	    <xsl:template match="/">

		<xsl:apply-templates select="ids"/> 

	    </xsl:template> 

	    <xsl:template match="ids">

		<document>

		    <template pageSize="21cm,29.7cm">

		        <pageTemplate>

		            <frame id="col1" x1="2cm" y1="2.4cm" width="8cm" height="26cm"/> 
		            <frame id="col2" x1="11cm" y1="2.4cm" width="8cm" height="26cm"/> 

		        </pageTemplate> 

		    </template> 

		<stylesheet>

		    <blockTableStyle id="ids"> 

		        <blockFont name="Helvetica-BoldOblique" size="12" start="0,0" stop="-1,0"/> 
		        <lineStyle kind="BOX" colorName="black" start="0,0" stop="-1,0"/> 

		        <lineStyle kind="BOX" colorName="black" start="0,0" stop="-1,-1"/> 

		    </blockTableStyle> 

		</stylesheet> 

		<story>

		    <blockTable colWidths="2cm, 6cm" repeatRows="1" style="ids">

		        <tr>

		            <td t="1">Ref.</td> 
		            <td t="1">Name</td> 

		        </tr> 
		        <xsl:apply-templates select="id"/> 

		    </blockTable> 

		</story> 
		</document> 

	    </xsl:template> 

	    <xsl:template match="id">

		<tr>

		    <td><xsl:value-of select="ref"/></td> 
		    <td><para><xsl:value-of select="name"/></para></td> 

		</tr> 

	    </xsl:template> 
	    </xsl:stylesheet> 

**Resulting RML file (generated)**
::

	<?xml version="1.0"?>

	    <document> 
	    ...

		<story>

		    <blockTable colWidths="2cm, 6cm" repeatRows="1" style="ids">

		        <tr>

		            <td t="1">Ref.</td> 
		            <td t="1">Name</td> 

		        </tr> 
		        <tr>

		            <td>pnk00</td> 
		            <td><para>Tiny sprl</para></td> 

		        </tr> 
		        <tr>

		            <td></td> 
		            <td><para>ASUS</para></td> 

		        </tr> 
		        <tr>

		            <td></td> 
		            <td><para>Agrolait</para></td> 

		        </tr> 
		        <tr>

		            <td></td> 
		            <td><para>Banque Plein-Aux-As</para></td> 

		        </tr> 
		        <tr>

		            <td></td> 
		            <td><para>China Export</para></td> 

		        </tr> 
		        <tr>

		            <td></td> 
		            <td><para>Ditrib PC</para></td> 

		        </tr> 
		        <tr>

		            <td></td> 
		            <td><para>Ecole de Commerce de Liege</para></td> 

		        </tr> 
		        <tr>

		            <td></td> 
		            <td><para>Elec Import</para></td> 

		        </tr> 
		        <tr>

		            <td></td> 
		            <td><para>Maxtor</para></td> 

		        </tr> 
		        <tr>

		            <td></td> 
		            <td><para>Mediapole SPRL</para></td> 

		        </tr> 
		        <tr>

		            <td>os</td> 
		            <td><para>Opensides sprl</para></td> 

		        </tr> 
		        <tr> 
		        <td></td>

		            <td><para>Tecsas sarl</para></td> 

		        </tr> 

		    </blockTable> 

		</story> 

	    </document> 

For more information on the formats used:

    * `RML user guide`_
    * `XSL specification`_ 
    * `XSL tutorial`_  

All these formats are extensions of the `XML specification`_.

.. _RML user guide: http://www.reportlab.com/docs/rml2pdf-userguide.pdf  
.. _XSL specification: http://www.w3.org/TR/xslt
.. _XSL tutorial: http://www.zvon.org/xxl/XSLTutorial/Books/Output/contents.html
.. _XML specification: http://www.w3.org/XML/

XML Template
------------

XML templates are simple XML files describing which fields among all available object fields are necessary for the report.

File format
"""""""""""

Tag names can be chosen arbitrarily (it must be valid XML though). In the XSL file, you will have to use those names. Most of the time, the name of a tag will be the same as the name of the object field it refers to.

Nodes without **type** attribute are transferred identically into the XML destination file (the data file). Nodes with a type attribute will be parsed by the server and their content will be replaced by data coming from objects. In addition to the type attribute, nodes have other possible attributes. These attributes depend on the type of the node (each node type supports or needs different attributes). Most node types have a name attribute, which refers to the  **name** of a field of the object on which we work.

As for the "browse" method on objects, field names in reports can use a notation similar to the notation found in object oriented programming languages. It means that "relation fields" can be used as "bridges" to fetch data from other (related) objects.

Let's use the "account.transfer" object as an example. It contains a partner_id field. This field is a relation field ("many to one") pointing to the "res.partner" object. Let's suppose that we want to create a report for transfers and in this report, we want to use the name of the recipient partner. This name could be accessed using the following expression as the name of the field:

    partner_id.name 

Possible types
""""""""""""""

Here is the list of available field types:

    * **field**: It is the simplest type. For nodes of this type, the server replaces the node content by the value of the field whose name is given in the name attribute. 

    * **fields**: when this type of node is used, the server will generate a node in the XML data file for each unique value of the field whose name is given in the name attribute. 

    Notes:

        ** This node type is often used with "id" as its name attribute. This has the effect of creating one node for each resource selected in the interface by the user. 
        ** The semantics of a node <node type="fields" name="field_name"> is similar to an SQL statement of the form "SELECT FROM object_table WHERE id in identifier_list **GROUP BY** field_name" where identifier_list is the list of ids of the resources selected by the ::user (in the interface). 

    * **eval**: This node type evaluate the expression given in the *expr* attribute. This expression may be any Python expression and may contain objects fields names. 

    * **zoom**: This node type allows to "enter" into the resource referenced by the relation field whose name is given in the name attribute. It means that its child nodes will be able to access the fields of that resource without having to prefix them with the field name that makes the link with the other object. In our example above, we could also have accessed the field name of the partner with the following: 

  ::

	<partner type="zoom" name="partner_id">

		<name type="field" name="name"/> 

	</partner> 

	In this precise case, there is of course no point in using this notation instead of the standard notation below: 

	<name type="field" name="partner_id.name"/> 

The **zoom** type is only useful when we want to recover several fields in the same object.

    * **function**: returns the result of the call to the function whose name is given in the name attribute. This function must be part of the list of predefined functions. For the moment, the only available function is today, which returns the current date. 

    * **call**: calls the object method whose name is given in the name attribute with the arguments given in the args attribute. The result is stored into a dictionary of the form {'name_of_variable': value, ... } and can be accessed through child nodes. These nodes must have a value attribute which correspond to one of the keys of the dictionary returned by the method. 

**Example**:
::

	<cost type="call" name="compute_seller_costs" args="">

	    <name value="name"/> 
	    <amount value="amount"/> 

	</cost> 

**TODO**: documenter format methode appellée def compute_buyer_costs(self, cr, uid, ids, \*args):

    * **attachment**: extract the first attachment of the resource whose id is taken from the field whose name is given in the name attribute, and put it as an image in the report. 

Example:
	<image type="attachment" name="id"/> 

**Example**


Here is an example of XML file:
::

	    <?xml version="1.0" encoding="ISO-8859-1"?> 
	    <transfer-list>

		<transfer type="fields" name="id">

		    <name type="field" name="name"/> 
		    <partner_id type="field" name="partner_id.name"/> 
		    <date type="field" name="date"/> 
		    <type type="field" name="type"/> 
		    <reference type="field" name="reference"/> 
		    <amount type="field" name="amount"/> 
		    <change type="field" name="change"/> 

		</transfer> 

	    </transfer-list> 


Introduction to RML
-------------------

For more information on the RML format, please refer to the official Reportlab documentation.

    * http://www.reportlab.com/docs/RML_UserGuide.pdf 

XSL:RML Stylesheet
------------------

There are two possibilities to do a XSL style sheet for a report. Either making everything by yourself, or use our predefined templates

Either freestyle or use corporate_defaults + rml_template

    import rml_template.xsl 

        required templates:

            - frames? 
            - stylesheet 
            - story 

        optional templates: 

Translations
""""""""""""

As OpenERP can be used in several languages, reports must be translatable. But in a report, everything doesn't have to be translated : only the actual text has to be translated, not the formatting codes. A field will be processed by the translation system if the XML tag which surrounds it (whatever it is) has a t="1" attribute. The server will translate all the fields with such attributes in the report generation process.

Useful links:
"""""""""""""

    * http://www.reportlab.com/docs/RML_UserGuide.pdf RML UserGuide (pdf) (reportlab.com) 

    * http://www.zvon.org/xxl/XSLTutorial/Output/index.html XSL Tutorial (zvon.org)
    * http://www.zvon.org/xxl/XSLTreference/Output/index.html XSL Reference (zvon.org)
    * http://www.w3schools.com/xsl/ XSL tutorial and references (W3Schools)
    * http://www.w3.org/TR/xslt/ XSL Specification (W3C) 


Example (with corporate defaults):
"""""""""""""""""""""""""""""""""""
::

	    <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" :xmlns:fo="http://www.w3.org/1999/XSL/Format">

		<xsl:import href="../../custom/corporate_defaults.xsl"/> 
		<xsl:import href="../../base/report/rml_template.xsl"/> 
		<xsl:variable name="page_format">a4_normal</xsl:variable> 
		<xsl:template match="/">

		    <xsl:call-template name="rml"/> 

		</xsl:template> 
		<xsl:template name="stylesheet">

		    </xsl:template> 

		<xsl:template name="story">

		    <xsl:apply-templates select="transfer-list"/> 

		</xsl:template> 
		<xsl:template match="transfer-list">

		    <xsl:apply-templates select="transfer"/> 

		</xsl:template> 
		<xsl:template match="transfer">

		    <setNextTemplate name="other_pages"/> 
		    <para>

		        Document: <xsl:value-of select="name"/> 

		    </para><para>

		        Type: <xsl:value-of select="type"/> 

		    </para><para>

		        Reference: <xsl:value-of select="reference"/> 

		    </para><para>

		        Partner ID: <xsl:value-of select="partner_id"/> 

		    </para><para>

		        Date: <xsl:value-of select="date"/> 

		    </para><para>

		        Amount: <xsl:value-of select="amount"/> 

		    </para> 
		    <xsl:if test="number(change)>0">

		        <para>

		            Change: <xsl:value-of select="change"/> 

		        </para> 

		    </xsl:if> 
		    <setNextTemplate name="first_page"/> 
		    <pageBreak/> 

		</xsl:template> 

	    </xsl:stylesheet> 



Reports without corporate header 
================================


**Example (with corporate defaults):**
::

	<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" :xmlns:fo="http://www.w3.org/1999/XSL/Format">
	     <xsl:import href="../../base/report/rml_template.xsl"/>
	     <xsl:variable name="page_format">a4_normal</xsl:variable>
	 
	     <xsl:template match="/">
		  <xsl:call-template name="rml"/>
	     </xsl:template>
	 
	     <xsl:template name="stylesheet">
	      </xsl:template>
	  
	      <xsl:template name="story">
		   <xsl:apply-templates select="transfer-list"/>
	      </xsl:template>
	  
	      <xsl:template match="transfer-list">
		   <xsl:apply-templates select="transfer"/>
	      </xsl:template>
	  
	      <xsl:template match="transfer">
		   <setNextTemplate name="other_pages"/>
	   
		   <para>
		         Document: <xsl:value-of select="name"/>
		   </para><para>
		         Type: <xsl:value-of select="type"/>
		   </para><para>
		         Reference: <xsl:value-of select="reference"/>
		   </para><para>
		         Partner ID: <xsl:value-of select="partner_id"/>
		   </para><para>
		         Date: <xsl:value-of select="date"/>
		   </para><para>
		         Amount: <xsl:value-of select="amount"/>
		   </para>
	   
		   <xsl:if test="number(change)>0">
		        <para>
		              Change: <xsl:value-of select="change"/>
		        </para>
		   </xsl:if>
	   
		   <setNextTemplate name="first_page"/> 
		  <pageBreak/>
	     </xsl:template>
	</xsl:stylesheet>


Each report with its own corporate header 
=========================================

**Example (with corporate defaults):**
::

	    <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" :xmlns:fo="http://www.w3.org/1999/XSL/Format">

		<xsl:import href="../../custom/corporate_defaults.xsl"/> 
		<xsl:import href="../../base/report/rml_template.xsl"/> 
		<xsl:variable name="page_format">a4_normal</xsl:variable> 
		..................... 
		</xsl:template> 

	    </xsl:stylesheet> 


Bar Codes 
=========

Barcodes in RML files
---------------------

Barcodes can be generated using the <barCode> tag in RML files. The following formats are supported:

    * codabar
    * code11
    * code128 (default if no 'code' specified')
    * standard39
    * standard93
    * i2of5
    * extended39
    * extended93
    * msi
    * fim
    * postnet 
    * ean13
    * ean8
    * usps_4state
                                        
  
You can change the following attributes for rendering your barcode:

    * 'code': 'char'
    * 'ratio':'float'
    * 'xdim':'unit'
    * 'height':'unit'
    * 'checksum':'bool'
    * 'quiet':'bool' 

Examples:

    <barcode code="code128" xdim="28cm" ratio="2.2">`SN12345678</barcode> 

How to add a new report
=======================

In 4.0.X

    Administration -> Custom -> Low Level -> Base->Actions -> ir.actions.report.xml 

Usual TAGS
==========

Code within [[ ]] tags is python code
-------------------------------------

The context of the code (the variable's values you can use) is the same as that 
described for :ref:`dynamic-report-content`.

Unicode reports 
===============

As of OpenERP 5.0-rc3 unicode printing with ReportLab is still not available. The problem is that OpenERP uses the PDF standard fonts (14 fonts, they are not embedded in the document but the reader provides them) that are Type1 and have only Latin1 characters.

The solution consists of 3 parts
--------------------------------

    * Provide TrueType fonts and make them accessible for ReportLab.
    * Register the TrueType fonts with ReportLab before using them in the reports.
    * Replace the old fontNames in xsl and rml templates with the TrueType ones. 

All these ideas are taken from the forums
-----------------------------------------

**Free TrueType fonts**

that can be used for this purpose are in the DejaVu family. http://dejavu-fonts.org/wiki/index.php?title=Main_Page They can be installed

    * in the ReportLab's fonts directory,
    * system-wide and include that directory in rl_config.py,
    * in a subdirectory of the OpenERP installation and give that path to ReportLab during the font registration. 

**In the server/bin/report/render/rml2pdf/__init__.py**
::

	import reportlab.rl_config
	reportlab.rl_config.warnOnMissingFontGlyphs = 0

	from reportlab.pdfbase import pdfmetrics
	from reportlab.pdfbase.ttfonts import TTFont
	import reportlab

	enc = 'UTF-8'

	#repeat these for all the fonts needed
	pdfmetrics.registerFont(TTFont('DejaVuSans', 'DejaVuSans.ttf',enc))
	pdfmetrics.registerFont(TTFont('DejaVuSans-Bold', 'DejaVuSans-Bold.ttf',enc))

	from reportlab.lib.fonts import addMapping

	#repeat these for all the fonts needed
	addMapping('DejaVuSans', 0, 0, 'DejaVuSans') #normal
	addMapping('DejaVuSans-Bold', 1, 0, 'DejaVuSans') #normal


trml2pdf.py should be modified to load this if invoked from the command line.

**All the xsl and rml files have to be modified**

A list of possible alternatives:
::

	'Times-Roman',       'DejaVuSerif.ttf'
	'Times-BoldItalic',  'DejaVuSerif-BoldItalic.ttf'
	'Times-Bold',        'DejaVuSerif-Bold.ttf'
	'Times-Italic',      'DejaVuSerif-Italic.ttf'

	'Helvetica',     'DejaVuSans.ttf'
	'Helvetica-BoldItalic',  'DejaVuSans-BoldOblique.ttf'
	'Helvetica-Bold',    'DejaVuSans-Bold.ttf'
	'Helvetica-Italic',  'DejaVuSans-Oblique.ttf'

	'Courier',           'DejaVuSansMono.ttf'
	'Courier-Bold',      'DejaVuSansMono-Bold.ttf'
	'Courier-BoldItalic','DejaVuSansMono-BoldOblique.ttf'
	'Courier-Italic',    'DejaVuSansMono-Oblique.ttf'

	'Helvetica-ExtraLight',  'DejaVuSans-ExtraLight.ttf'

	'TimesCondensed-Roman',      'DejaVuSerifCondensed.ttf'
	'TimesCondensed-BoldItalic', 'DejaVuSerifCondensed-BoldItalic.ttf'
	'TimesCondensed-Bold',       'DejaVuSerifCondensed-Bold.ttf'
	'TimesCondensed-Italic',     'DejaVuSerifCondensed-Italic.ttf'

	'HelveticaCondensed',        'DejaVuSansCondensed.ttf'
	'HelveticaCondensed-BoldItalic', 'DejaVuSansCondensed-BoldOblique.ttf'
	'HelveticaCondensed-Bold',   'DejaVuSansCondensed-Bold.ttf'
	'HelveticaCondensed-Italic', 'DejaVuSansCondensed-Oblique.ttf


