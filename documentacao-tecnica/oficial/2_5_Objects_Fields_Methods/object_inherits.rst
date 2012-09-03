
.. _inherits-link:

Inheritance by Delegation - _inherits
=====================================

 **Syntax :**::

    class tiny_object(osv.osv)
        _name = 'tiny.object'
        _table = 'tiny_object'
        _inherits = {
            'tiny.object_a': 'object_a_id',
            'tiny.object_b': 'object_b_id',
            ... ,
            'tiny.object_n': 'object_n_id'
        }
        (...)

The object 'tiny.object' inherits from all the columns and all the methods from
the n objects 'tiny.object_a', ..., 'tiny.object_n'.

To inherit from multiple tables, the technique consists in adding one column to
the table tiny_object per inherited object. This column will store a foreign
key (an id from another table). The values *'object_a_id' 'object_b_id' ...
'object_n_id'* are of type string and determine the title of the columns in
which the foreign keys from 'tiny.object_a', ..., 'tiny.object_n' are stored.

This inheritance mechanism is usually called " *instance inheritance* "  or  "
*value inheritance* ". A resource (instance) has the VALUES of its parents. 

