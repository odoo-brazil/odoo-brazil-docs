Inheritance in Views 
==================== 

When you create and inherit objects in some custom or specific modules, it is better to inherit (than to replace) from an existing view to add/modify/delete some fields and preserve the others.

:Example:

.. code-block:: xml

	<record model="ir.ui.view" id="view_partner_form">
	    <field name="name">res.partner.form.inherit</field>
	    <field name="model">res.partner</field>
	    <field name="inherit_id" ref="base.view_partner_form"/>
	    <field name="arch" type="xml">
	        <notebook position="inside">
	            <page string="Relations">
	                <field name="relation_ids" colspan="4" nolabel="1"/>
	            </page>
	        </notebook>
	    </field>
	</record>

This will add a page to the notebook of the ``res.partner.form`` view in the 
base module.

The inheritance engine will parse the existing view and search for the root nodes of

.. code-block:: xml

	<field name="arch" type="xml">

It will append or edit the content of this tag. If this tag has some attributes, 
it will look in the parent view for a node with matching attributes (except 
position).

You can use these values in the position attribute:

    * inside (default): your values will be appended inside the tag
    * after: add the content after the tag
    * before: add the content before the tag
    * replace: replace the content of the tag. 

Replacing Content
~~~~~~~~~~~~~~~~~

.. code-block:: xml

	<record model="ir.ui.view" id="view_partner_form1">
	    <field name="name">res.partner.form.inherit1</field>
	    <field name="model">res.partner</field>
	    <field name="inherit_id" ref="base.view_partner_form"/>
	    <field name="arch" type="xml">
	        <page string="Extra Info" position="replace">
	            <field name="relation_ids" colspan="4" nolabel="1"/>
	        </page>
	    </field>
	</record>

Will replace the content of the Extra Info tab of the notebook with the ``relation_ids`` field.

The parent and the inherited views are correctly updated with ``--update=all`` argument like any other views.

Deleting Content
~~~~~~~~~~~~~~~~

To delete a field from a form, an empty element with ``position="replace"`` attribute is used. Example:

.. code-block:: xml

	<record model="ir.ui.view" id="view_partner_form2">
	    <field name="name">res.partner.form.inherit2</field>
	    <field name="model">res.partner</field>
	    <field name="inherit_id" ref="base.view_partner_form"/>
	    <field name="arch" type="xml">
	        <field name="lang" position="replace"/>
	    </field>
	</record>

Inserting Content
~~~~~~~~~~~~~~~~~

To add a field into a form before the specified tag use ``position="before"`` attribute. 

.. code-block:: xml

	<record model="ir.ui.view" id="view_partner_form3">
	    <field name="name">res.partner.form.inherit3</field>
	    <field name="model">res.partner</field>
	    <field name="inherit_id" ref="base.view_partner_form"/>
	    <field name="arch" type="xml">
	        <field name="lang" position="before">
	            <field name="relation_ids"/>
	        </field>
	    </field>
	</record>
	
Will add ``relation_ids`` field before the ``lang`` field.	

To add a field into a form after the specified tag use ``position="after"`` attribute. 

.. code-block:: xml

	<record model="ir.ui.view" id="view_partner_form4">
	    <field name="name">res.partner.form.inherit4</field>
	    <field name="model">res.partner</field>
	    <field name="inherit_id" ref="base.view_partner_form"/>
	    <field name="arch" type="xml">
	        <field name="lang" position="after">
	            <field name="relation_ids"/>
	        </field>
	    </field>
	</record>
	
Will add ``relation_ids`` field after the ``lang`` field.


Multiple Changes
~~~~~~~~~~~~~~~~

To make changes in more than one location, wrap the fields in a data element.

.. code-block:: xml

    <record model="ir.ui.view" id="view_partner_form5">
        <field name="name">res.partner.form.inherit5</field>
        <field name="model">res.partner</field>
        <field name="inherit_id" ref="base.view_partner_form"/>
        <field name="arch" type="xml">
            <data>
                <field name="lang" position="replace"/>
                <field name="website" position="after">
                    <field name="lang"/>
                </field>
            </data>
        </field>
    </record>

Will delete the ``lang`` field from its usual location, and display it after
the ``website`` field.

.. _xpath-element-inheritance:

XPath Element
~~~~~~~~~~~~~

Sometimes a view is too complicated to let you simply identify a target field
by name. For example, the field might appear in two places. When that happens,
you can use an ``xpath`` element to describe where your changes should be 
placed. 

.. code-block:: xml

    <record model="ir.ui.view" id="view_partner_form6">
        <field name="name">res.partner.form.inherit6</field>
        <field name="model">res.partner</field>
        <field name="inherit_id" ref="base.view_partner_form"/>
        <field name="arch" type="xml">
            <data>
                <xpath 
                    expr="//field[@name='address']/form/field[@name='email']"
                    position="after">
                    <field name="age"/>
                </xpath>
                <xpath 
                    expr="//field[@name='address']/tree/field[@name='email']"
                    position="after">
                    <field name="age"/>
                </xpath>
            </data>
        </field>
    </record>
    
Will add the ``age`` field after the ``email`` field in both the form and tree 
view of the address list.       
