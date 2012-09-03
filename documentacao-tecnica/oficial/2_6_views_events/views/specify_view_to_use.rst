Specify the views you want to use
=================================

There are some cases where you would like to specify a view other than the default:

- If there are several form or tree views for an object.
- If you want to change the form or tree view used by a relational field 
  (one2many for example).

Using the priority field
------------------------

This field is available in the view definition, and is 16 by default. By 
default, OpenERP will display a model using the view with the highest priority
(the smallest number). For example, imagine we have two views for a simple model.
The model *client* with two fields : **firstname** and **lastname**. We will define
two views, one which shows the firstname first, and the other one which shows 
the lastname first.

.. code-block:: xml
    :linenos:

    <!--
        Here is the first view for the model 'client'.
        We don't specify a priority field, which means 
        by default 16.
    -->
    <record model="ir.ui.view" id="client_form_view_1">
        <field name="name">client.form.view1</field>
        <field name="model">client</field>
        <field name="type">form</fiel>
        <field name="arch" type="xml">
            <field name="firstname"/>
            <field name="lastname"/>
        </field>
    </record>

    <!--
        A second view, which show fields in an other order.
        We specify a priority of 15.
    -->
    <record model="ir.ui.view" id="client_form_view_2">
        <field name="name">client.form.view2</field>
        <field name="model">client</field>
        <field name="priority" eval="15"/>
        <field name="type">form</fiel>
        <field name="arch" type="xml">
            <field name="lastname"/>
            <field name="firstname"/>
        </field>
    </record>

Now, each time OpenERP will have to show a form view for our object *client*, it will have the choice between two views.
**It will always use the second one, because it has a higher priority !** Unless you tell it to use the first one !

Specify per-action view
-----------------------

To illustrate this point, we will create 2 menus which show a form view for this *client* object :

.. code-block:: xml
    :linenos:

    <!--
        This action open the default view (in our case,
        the view with the highest priority, the second one)
    -->
    <record 
    	model="ir.actions.act_window" 
    	id="client_form_action">
        <field name="name">client.form.action</field>
        <field name="res_model">client</field>
        <field name="view_type">form</field>
        <field name="view_mode">form</field>
    </record>

    <!--
        This action open the view we specify.
    -->
    <record 
    	model="ir.actions.act_window" 
    	id="client_form_action1">
        <field name="name">client.form.action1</field>
        <field name="res_model">client</field>
        <field name="view_type">form</field>
        <field name="view_mode">form</field>
        <field name="view_id" ref="client_form_view_1"/>
    </record>

    <menuitem id="menu_id" name="Client main menu"/>
    <menuitem 
    	id="menu_id_1" 
    	name="Here we don't specify the view"
        action="client_form_action" parent="menu_id"/>
    <menuitem 
    	id="menu_id_1" 
    	name="Here we specify the view"
        action="client_form_action1" parent="menu_id"/>

As you can see on line *19*, we can specify a view. That means that when we open 
the second menu, OpenERP will use the form view *client_form_view_1*, regardless
of its priority.

.. note::

    Remember to use the module name (*module.view_id*) in the *ref* attribute if 
    you are referring to a view defined in another module.

Specify views for related fields
--------------------------------

Using the context
~~~~~~~~~~~~~~~~~

The *view_id* method works very well for menus/actions, but how can you specify the view to use for a one2many
field, for example? When you have a one2many field, two views are used, a tree view (**in blue**), and a form view when
you click on the add button (**in red**).

.. figure::  images/one2many_views.png
    :scale: 70%
    :align: center

When you add a one2many field in a form view, you do something like this :

.. code-block:: xml

    <field name="order_line" colspan="4" nolabel="1"/>

If you want to specify the views to use, you can add a *context* attribute, and
specify a view id for each type of view supported, exactly like the action's 
*view_id* attribute:

.. code-block:: xml

    <field name="order_line" colspan="4" nolabel="1"
           context="{'form_view_ref' : 'module.view_id', 'tree_view_ref' : 'model.view_id'}"/>

If you don't specify the views, OpenERP will choose one in this order :

1. It will use the <form> or <tree> view defined **inside** the field (see below)
2. Else, it will use the views with the highest priority for this object.
3. Finally, it will generate default empty views, with all fields.

.. note::

    The context keys are named <view_type>_view_ref.

.. note::

    By default, OpenERP will never use a view that is not defined for your object. If you have two models, with the
    same fields, but a different model name, OpenERP will never use the view of one for the other,
    even if one model inherit an other.

    You can force this by manually specifying the view, either in the action or in the context.

Using subviews
~~~~~~~~~~~~~~

In the case of relational fields, you can create a view directly inside a field :

.. code-block:: xml

    <record model="ir.ui.view" id="some_view">
        <field name="name">some.view</field>
        <field name="type">form</field>
        <field name="model">some.model.with.one2many</field>
        <field name="arch" type="xml">
            <field name="..."/>
            
            <!-- <=== order_line is a one2many field -->
            <field name="order_line" colspan="4" nolabel="1">
                <form>
                    <field name="qty"/>
                    ...
                </form>
                <tree>
                    <field name="qty"/>
                    ...
                </tree>
            </field>
    </field>

If you or another developer want to inherit from this view in another module,
you need to inherit from the parent view and then modify the child fields.
With child views, you'll often need to use an :ref:`xpath-element-inheritance`
to describe exactly where to place your new fields.

.. code-block:: xml

    <record model="ir.ui.view" id="some_inherited_view">
        <field name="name">some.inherited.view</field>
        <field name="type">form</field>
        <field name="model">some.model.with.one2many</field>
        <field name="inherit_id" ref="core_module.some_view"/>
        <field name="arch" type="xml">
            <data>
                <xpath 
                   expr="//field[@name='order_line']/form/field[@name='qty']"
                   position="after">
                   <field name="size"/>
                </xpath>
                <xpath 
                   expr="//field[@name='order_line']/tree/field[@name='qty']"
                   position="after">
                   <field name="size"/>
                </xpath>
            </data>
    </field>

One down side of defining a subview like this is that it can't be inherited on
its own, it can only be inherited with the parent view. Your views will be more
flexible if you define the child views separately and then specify which child
view to use as part of the one2many field.
