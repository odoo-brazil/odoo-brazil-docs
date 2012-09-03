Gantt Views
===========

Gantt view provides timeline view for the data. Generally, it can be used to display
project tasks and resource allocation.

A Gantt chart is a graphical display of all the tasks that a project is composed of.
Each bar on the chart is a graphical representation of the length of time the task is
planned to take.

A resource allocation summary bar is shown on top of all the grouped tasks,
representing how effectively the resources are allocated among the tasks.

Color coding of the summary bar is as follows:

    * `Gray` shows that the resource is not allocated to any task at that time    	
    * `Blue` shows that the resource is fully allocated at that time.
    * `Red` shows that the resource is overallocated

View Specification
------------------

Here is an example view:

.. code-block:: xml

    <gantt color="user_id" date_delay="planned_hours" date_start="date_start" string="Tasks">
        <level object="project.project" link="project_id" domain="[]">
            <field name="name"/>
        </level>
    </gantt>

The ``attributes`` accepted by the ``gantt`` tag are similar to ``calendar`` view tag. The
``level`` tag is used to group the records by some ``many2one`` field. Currently, only
one level is supported.

Here is the list of supported attributes for ``gantt`` tag:

    ``string``
        The title string for the view.

    ``date_start``
        A ``datetime`` field to specify the starting date for the gantt item. This 
        attribute is required.
        
    ``date_stop``
        A ``datetime`` field to specify the end date. Ignored if ``date_delay`` 
        attribute is specified.
        
    ``date_delay``
        A ``numeric`` field to specify time in hours for a record. This attribute
        will get preference over ``date_stop`` and ``date_stop`` will be ignored.
        
    ``day_length``
        An ``integer`` value to specify working day length. Default is ``8`` hours.
        
    ``color``
        A field, generally ``many2one``, to colorize calendar/gantt items.
        
    ``mode``
        A string value to set default view/zoom mode. For ``gantt`` view, this can be
        one of following (default is ``month``):
        
        * ``day``
        * ``3days``
        * ``week``
        * ``3weeks``
        * ``month``
        * ``3months``
        * ``year``
        * ``3years``
        * ``5years``

The ``level`` tag supports following attributes:

    ``object``
        An openerp object having many2one relationship with view object.

    ``link``
        The field name in current object that links to the given ``object``.

    ``domain``
        The domain to be used to filter the given ``object`` records.


Drag and Drop
-------------

The left side pane displays list of the tasks grouped by the given ``level`` field.
You can reorder or change the group of any records by dragging them.

The main content pane displays horizontal bars plotted on a timeline grid. A group
of bars are summarized with a top summary bar displaying resource allocation of all
the underlying tasks.

You can change the task start time by dragging the tasks horizontally. While
end time can be changed by dragging right end of a bar.

.. note::

    The time is calculated considering ``day_length`` so a bar will span more
    then one day if total time for a task is greater then ``day_length`` value.
    
Screenshots
-----------
    
.. figure::  images/gantt.png
    :scale: 50%
    :align: center

