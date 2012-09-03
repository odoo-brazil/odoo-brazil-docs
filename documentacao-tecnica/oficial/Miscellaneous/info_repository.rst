Information Repository
======================

The information repository is a semantics tree in which the data that are not the resources are stored. We find in this structure:

   1. the values by default
   2. the conditional values;
          * the state depends on the zip code,
          * the payment method depends of the partner, ...
   3. the reactions to the events client;
          * click on the invoice menu,
          * print an invoice,
          * action on a partner, ...

The IR has 3 methods;

    * add a value in the tree
    * delete a value in the tree
    * obtain all the values of a selected sheet


Setting Value
-------------

The ir_set tag allows you to insert new values in the  "Information
Repository". This tag must contain several *field* tags with *name* and *eval*
attributes.

The attributes are those defined by the access methods to the information
repository. We must provide it with several attributes: *keys*, *args*, *name*,
*value*, *isobject*, *replace*, *meta* and some optional fields.

Example:

.. code-block:: xml

    <ir_set>
        <field name="keys" eval="[('action','client_print_multi'),('res_model','account.invoice')]"/>
        <field name="args" eval="[]"/>
        <field name="name">Print Invoices</field>
        <field name="value" eval="'ir.actions.report.xml,'+str(l0)"/>
        <field name="isobject" eval="True"/>
        <field name="replace" eval="False"/>
    </ir_set>


IR Methods
-----------

.. code-block:: python

    def ir_set(cr, uid, key, key2, name, models, value, replace=True, isobject=False, meta=None)

.. code-block:: python

    def ir_get(cr, uid, key, key2, models, meta=False, context={}, res_id_req=False)

.. code-block:: python

    def ir_del(cr, uid, id):


:Description of the fields:

   1. key:
   2. key2:
   3. name:
   4. models:
   5. value:
   6. isobject:
   7. replace: whether or not the action described should override an existing action or be appended to the list of actions.
   8. meta:

:Using ir_set and ir_get:

.. code-block:: python

    ...

        res = ir.ir_set(cr, uid, key, key2, name, models, value, replace, isobject, meta)

    ...


    ...

        if not report.menu_id:

            ir.ir_set(cr, uid, 'action', 'client_print_multi', name, [(model, False)], action, False, True)

        else:

            ir.ir_set(cr, uid, 'action', 'tree_but_open', 'Menuitem', [('ir.ui.menu', int(m_id))], action, False, True)

    ...


    ...

        res = ir.ir_get(cr, uid, [('default', self._name), ('field', False)], [('user_id',str(uid))])

    ...

        account_payable = ir.ir_get(cr, uid, [('meta','res.partner'), ('name','account.payable')], opt)[0][2]

    ...

