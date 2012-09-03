Action creation
===============
  
Linking events to action
-------------------------

The available type of events are:

    * **client_print_multi** (print from a list or form)
    * **client_action_multi** (action from a list or form)
    * **tree_but_open** (double click on the item of a tree, like the menu)
    * **tree_but_action** (action on the items of a tree) 

To map an events to an action:

.. code-block:: xml

    <record model="ir.values" id="ir_open_journal_period">
        <field name="key2">tree_but_open</field>
        <field name="model">account.journal.period</field>
        <field name="name">Open Journal</field>
        <field name="value" eval="'ir.actions.wizard,%d'%action_move_journal_line_form_select"/>
        <field name="object" eval="True"/>
    </record>

If you double click on a journal/period (object: account.journal.period), this will open the selected wizard. (id="action_move_journal_line_form_select").

You can use a res_id field to allow this action only if the user click on a specific object.

.. code-block:: xml

    <record model="ir.values" id="ir_open_journal_period">
        <field name="key2">tree_but_open</field>
        <field name="model">account.journal.period</field>
        <field name="name">Open Journal</field>
        <field name="value" eval="'ir.actions.wizard,%d'%action_move_journal_line_form_select"/>
        <field name="res_id" eval="3"/>
        <field name="object" eval="True"/>
    </record>

The action will be triggered if the user clicks on the account.journal.period n°3.

When you declare wizard, report or menus, the ir.values creation is automatically made with these tags:

  * <wizard... />
  * <menuitem... />
  * <report... /> 

So you usually do not need to add the mapping by yourself. 

