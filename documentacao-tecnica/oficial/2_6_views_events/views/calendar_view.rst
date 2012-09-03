Calendar Views
==============

Calendar view provides timeline/schedule view for the data.

View Specification
------------------

Here is an example view:

.. code-block:: xml

    <calendar color="user_id" date_delay="planned_hours" date_start="date_start" string="Tasks">
        <field name="name"/>
        <field name="project_id"/>
    </calendar>

Here is the list of supported attributes for ``calendar`` tag:

    ``string``
        The title string for the view.

    ``date_start``
        A ``datetime`` field to specify the starting date for the calendar item. This 
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
        A string value to set default view/zoom mode. For ``calendar`` view, this can be
        one of following (default is ``month``):
        
        * ``day``
        * ``week``
        * ``month``
   
Screenshots
-----------

Month Calendar:

.. figure::  images/calendar_month.png
    :scale: 50%
    :align: center

Week Calendar:
    
.. figure::  images/calendar_week.png
    :scale: 50%
    :align: center

