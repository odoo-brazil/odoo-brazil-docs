Search views
--------------

Search views are a new feature of OpenERP supported as of version 6.0 
It creates a customized search panel, and is declared quite similarly to a form view,
except that the view type and root element change to ``search`` instead of ``form``.

.. image:: images/search.png
   :scale: 50
   :align: center

Following is the list of new elements and features supported in search views.

Group tag
+++++++++

Unlike form group elements, search view groups support unlimited number of widget(fields or filters)
in a row (no automatic line wrapping), and only use the following attributes:

    + ``expand``: turns on the expander icon on the group (1 for expanded by default, 0 for collapsed)
    + ``string``: label for the group

.. code-block:: xml

    <group expand="1" string="Group By...">
       <filter string="Users" icon="terp-project" domain="[]" context="{'group_by':'user_id'}"/>
       <filter string="Project" icon="terp-project" domain="[]" context="{'group_by':'project_id'}"/>
       <separator orientation="vertical"/>
       <filter string="Deadline" icon="terp-project" domain="[]" context="{'group_by':'date_deadline'}"/>
    </group>

In the screenshot above the green area is an expandable group.

Filter tag
+++++++++++
Filters are displayed as a toggle button on search panel 
Filter elements can add new values in the current domain or context of the search view.
Filters can be added as a child element of field too, to indicate that they apply specifically
to that field (in this case the button's icon will smaller)

In the picture above the red area contains filters at the top of the form while
the blue area highlights a field and it's child filter.

.. code-block:: xml

    <filter string="Current" domain="[('state','in',('open','draft'))]" help="Draft, Open and Pending Tasks" icon="terp-project"/>
    <field name="project_id" select="1" widget="selection">
        <filter domain="[('project_id.user_id','=',uid)]" help="My Projects" icon="terp-project"/>
    </field>

Group By
++++++++

.. code-block:: xml

    <filter string="Project" icon="terp-project" domain="[]" context="{'group_by':'project_id'}"/>

Above filters groups records sharing the same ``project_id`` value. Groups are loaded
lazily, so the inner records are only loaded when the group is expanded.
The group header lines contain the common values for all records in that group, and all numeric
fields currently displayed in the view are replaced by the sum of the values in that group.

It is also possible to group on multiple values by specifying a list of fields instead of a single string.
In this case nested groups will be displayed::

    <filter string="Project" icon="terp-project" domain="[]" context="{'group_by': ['project_id', 'user_id'] }"/>

Fields
++++++

Field elements in search views are used to get user-provided values
for searches. As a result, as for group elements, they are quite
different than form view's fields:

* a search field can contain filters, which generally indicate that
  both field and filter manage the same field and are related.

  Those inner filters are rendered as smaller buttons, right next to
  the field, and *must not* have a ``string`` attribute.

* a search field really builds a domain composed of ``[(field_name,
  operator, field_value)]``. This domain can be overridden in two
  ways:

  * ``@operator`` replaces the default operator for the field (which
    depends on its type)

  * ``@filter_domain`` lets you provide a fully custom domain, which
    will replace the default domain creation

* a search field does not create a context by default, but you can
  provide an ``@context`` which will be evaluated and merged into the
  wider context (as with a ``filter`` element).

To get the value of the field in your ``@context`` or
``@filter_domain``, you can use the variable ``self``:

.. code-block:: xml

    <field name="location_id" string="Location"
           filter_domain="['|',('location_id','ilike',self),('location_dest_id','ilike',self)]"/>

or

.. code-block:: xml

    <field name="journal_id" widget="selection"
           context="{'journal_id':self, 'visible_id':self, 'normal_view':False}"/>

Range fields (date, datetime, time)
"""""""""""""""""""""""""""""""""""

The range fields are composed of two input widgets (from and two)
instead of just one.

This leads to peculiarities (compared to non-range search fields):

* It is not possible to override the operator of a range field via
  ``@operator``, as the domain is built of two sections and each
  section uses a different operator.

* Instead of being a simple value (integer, string, float) ``self``
  for use in ``@filter_domain`` and ``@context`` is a ``dict``.

  Because each input widget of a range field can be empty (and the
  field itself will still be valid), care must be taken when using
  ``self``: it has two string keys ``"from"`` and ``"to"``, but any of
  these keys can be either missing entirely or set to the value
  ``False``.

Actions for Search view
+++++++++++++++++++++++

After declaring a search view, it will be used automatically for all tree views on the same model.
If several search views exist for a single model, the one with the highest priority (lowest sequence) will
be used. Another option is to explicitly select the search view you want to use, by setting the
``search_view_id`` field of the action.

In addition to being able to pass default form values in the context of the action, OpenERP 6.0 now
supports passing initial values for search views too, via the context. The context keys need to match the
``search_default_XXX`` format. ``XXX`` may refer to the ``name`` of a ``<field>`` or ``<filter>``
in the search view (as the ``name`` attribute is not required on filters, this only works for filters that have
an explicit ``name`` set). The value should be either the initial value for search fields, or
simply a boolean value for filters, to toggle them 

.. code-block:: xml

    <record id="action_view_task" model="ir.actions.act_window">
        <field name="name">Tasks</field>
        <field name="res_model">project.task</field>
        <field name="view_type">form</field>
        <field name="view_mode">tree,form,calendar,gantt,graph</field>
        <field eval="False" name="filter"/>
        <field name="view_id" ref="view_task_tree2"/>
        <field name="context">{"search_default_current":1,"search_default_user_id":uid}</field>
        <field name="search_view_id" ref="view_task_search_form"/>
    </record>

Custom Filters
++++++++++++++

As of v6.0, all search views also features custom search filters, as show below.
Users can define their own custom filters using any of the fields available on the current model,
combining them with AND/OR operators. It is also possible to save any search context (the combination
of all currently applied domain and context values) as a personal filter, which can be recalled
at any time. Filters can also be turned into Shortcuts directly available in the User's homepage.

.. image:: images/filter.png
   :scale: 50
   :align: center


In above screenshot we filter Partner where Salesman = Demo user and Country = Belgium,
We can save this search criteria as a Shortcut or save as Filter.

Filters are user specific and can be modified via the Manage Filters option in the filters drop-down.
