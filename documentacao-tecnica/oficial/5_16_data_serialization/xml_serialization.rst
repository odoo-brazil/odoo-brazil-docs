
.. _xml-serialization:

XML Data Serialization
----------------------

Since version 4.2, OpenERP provides an XML-based data serialization format.

The basic format of an OpenERP XML file is as follows:

.. code-block:: xml

     <?xml version="1.0"?>
     <openerp>
         <data>
         <record model="model.name_1" id="id_name_1">
             <field name="field1">
                 field1 content
             </field>
             <field name="field2">
                 field2 content
             </field>
             (...)
         </record>
         <record model="model.name_2" id="id_name_2">
             (...)
         </record>
         (...)
         </data>
     </openerp>

Fields contents are strings that must be encoded as UTF-8 in XML files.

Let's review an example taken from the OpenERP source (base_demo.xml in the base module):

.. code-block:: xml

       <record model="res.company" id="main_company">
           <field name="name">OpenERP SA</field>
           <field name="partner_id" ref="main_partner"/>
           <field name="currency_id" ref="EUR"/>
       </record>

       <record model="res.users" id="user_admin">
           <field name="login">admin</field>
           <field name="password">admin</field>
           <field name="name">Administrator</field>
           <field name="signature">Administrator</field>
           <field name="action_id" ref="action_menu_admin"/>
           <field name="menu_id" ref="action_menu_admin"/>
           <field name="address_id" ref="main_address"/>
           <field name="groups_id" eval="[(6,0,[group_admin])]"/>
           <field name="company_id" ref="main_company"/>
       </record>

This last record defines the admin user :

    * The fields login, password, etc are straightforward.
    * The **ref** attribute allows to fill relations between the records :

.. code-block:: xml

    <field name="company_id" ref="main_company"/>

The``company_id`` field is a many-to-one relation from the user object to the company object, and **main_company** is the id of to associate.

    * The **eval** attribute allows to put some python code in the xml: here the groups_id field is a many2many. For such a field, "[(6,0,[group_admin])]" means : Remove all the groups associated with the current user and use the list [group_admin] as the new associated groups (and group_admin is the id of another record).

    * The **search** attribute allows to find the record to associate when you do not know its xml id. You can thus specify a search criteria to find the wanted record. The criteria is a list of tuples of the same form than for the predefined search method. If there are several results, an arbitrary one will be chosen (the first one):

    <field name="partner_id" search="[]" model="res.partner"/>

This is a classical example of the use of ``search`` in demo data: here we do not really care about which partner we want to use for the test, so we give an empty list. Notice the **model** attribute is currently mandatory.

Some typical XML elements are described below.


Record Tag
++++++++++

The addition of new data is made with the **record** tag. This one takes a mandatory attribute : **model**. Model is the object name where the insertion has to be done. The tag record can also take an optional attribute: **id**. If this attribute is given, a variable of this name can be used later on, in the same file, to make reference to the newly created resource ID.

A **record** tag may contain field tags. They indicate the record's **fields** value. If a field is not specified the default value will be used.

Example
~~~~~~~

.. code-block:: xml

    <record model="ir.actions.report.xml" id="l0">
         <field name="model">account.invoice</field>
         <field name="name">Invoices List</field>
         <field name="report_name">account.invoice.list</field>
         <field name="report_xsl">account/report/invoice.xsl</field>
         <field name="report_xml">account/report/invoice.xml</field>
    </record>

field tag
+++++++++

The attributes for the field tag are the following:

    * **name**
          o mandatory attribute indicating the field name
    * **eval**
          o python expression that indicating the value to add
    * **ref**
          o reference to an id defined in this file

function tag
++++++++++++

    * model:
    * name:
    * eval
          o should evaluate to the list of parameters of the method to be called, excluding cr and uid

Example
~~~~~~~

.. code-block:: xml

    <function 
    	model="ir.ui.menu" 
    	name="search" 
    	eval="[[('name','=','Operations')]]"/>

getitem tag
+++++++++++

Takes a subset of the evaluation of the last child node of the tag.

    * type
          - int or list
    * index
    * int or string (a key of a dictionary)

Example
~~~~~~~

Evaluates to the first element of the list of ids returned by the function node:

.. code-block:: xml

    <getitem index="0" type="list">
        <function 
        	model="ir.ui.menu" 
        	name="search" 
        	eval="[[('name','=','Operations')]]"/>
    </getitem>
