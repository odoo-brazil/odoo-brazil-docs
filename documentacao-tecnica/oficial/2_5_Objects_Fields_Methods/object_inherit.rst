
.. _inherit-link:

Object Inheritance - _inherit
=============================

Introduction
++++++++++++

Objects may be inherited in some custom or specific modules. It is better to
inherit an object to add/modify some fields.

It is done with::

    _inherit='object.name'

Extension of an object
++++++++++++++++++++++

There are two possible ways to do this kind of inheritance. Both ways result in
a new class of data, which holds parent fields and behaviour as well as
additional fields and behaviour, but they differ in heavy programatical
consequences.

While Example 1 creates a new subclass "custom_material" that may be "seen" or
"used" by any view or tree which handles "network.material", this will not be
the case for Example 2.

This is due to the table (other.material) the new subclass is operating on,
which will never be recognized by previous "network.material" views or trees.

Example 1::

    class custom_material(osv.osv):
        _name = 'network.material'
        _inherit = 'network.material'
        _columns = {
            'manuf_warranty': fields.boolean('Manufacturer warranty?'),
        }
        _defaults = {
            'manuf_warranty': lambda *a: False,
        }
        custom_material()

.. tip:: Notice

    _name == _inherit

In this example, the 'custom_material' will add a new field 'manuf_warranty' to
the object 'network.material'. New instances of this class will be visible by
views or trees operating on the superclasses table 'network.material'.

This inheritancy is usually called "class inheritance" in Object oriented
design. The child inherits data (fields) and behavior (functions) of his
parent.


Example 2::

    class other_material(osv.osv):
        _name = 'other.material'
        _inherit = 'network.material'
        _columns = {
            'manuf_warranty': fields.boolean('Manufacturer warranty?'),
        }
        _defaults = {
            'manuf_warranty': lambda *a: False,
        }
        other_material()

.. tip:: Notice

    _name != _inherit

In this example, the 'other_material' will hold all fields specified by
'network.material' and it will additionally hold a new field 'manuf_warranty'.
All those fields will be part of the table 'other.material'. New instances of
this class will therefore never been seen by views or trees operating on the
superclasses table 'network.material'.

This type of inheritancy is known as "inheritance by prototyping" (e.g.
Javascript), because the newly created subclass "copies" all fields from the
specified superclass (prototype). The child inherits data (fields) and behavior
(functions) of his parent.

