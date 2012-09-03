
.. _fields-link:

Fields Introduction
===================

Objects may contain different types of fields. Those types can be divided into
three categories: simple types, relation types and functional fields. The
simple types are integers, floats, booleans, strings, etc ... ; the relation
types are used to represent relations between objects (one2one, one2many,
many2one). Functional fields are special fields because they are not stored in
the database but calculated in real time given other fields of the view.

Here's the header of the initialization method of the class any field defined
in OpenERP inherits (as you can see in server/bin/osv/fields.py)::

    def __init__(self, string='unknown', required=False, readonly=False,
                 domain=None, context="", states=None, priority=0, change_default=False, size=None,
                 ondelete="set null", translate=False, select=False, **args) :

There are a common set of optional parameters that are available to most field
types:

:change_default: 
	Whether or not the user can define default values on other fields depending 
	on the value of this field. Those default values need to be defined in
	the ir.values table.
:help: 
	A description of how the field should be used: longer and more descriptive
	than `string`. It will appear in a tooltip when the mouse hovers over the 
	field.
:ondelete: 
	How to handle deletions in a related record. Allowable values are: 
	'restrict', 'no action', 'cascade', 'set null', and 'set default'.
:priority: Not used?
:readonly: `True` if the user cannot edit this field, otherwise `False`.
:required:
	`True` if this field must have a value before the object can be saved, 
	otherwise `False`.
:size: The size of the field in the database: number characters or digits.
:states:
	Lets you override other parameters for specific states of this object. 
	Accepts a dictionary with the state names as keys and a list of name/value 
	tuples as the values. For example: `states={'posted':[('readonly',True)]}`
:string: 
	The field name as it should appear in a label or column header. Strings
	containing non-ASCII characters must use python unicode objects. 
	For example: `'tested': fields.boolean(u'Testé')` 
:translate:
	`True` if the *content* of this field should be translated, otherwise 
	`False`.

There are also some optional parameters that are specific to some field types:

:context: 
	Define a variable's value visible in the view's context or an on-change 
	function. Used when searching child table of `one2many` relationship?
:domain: 
    Domain restriction on a relational field.

    Default value: []. 

    Example: domain=[('field','=',value)])
:invisible: Hide the field's value in forms. For example, a password.
:on_change:
	Default value for the `on_change` attribute in the view. This will launch
	a function on the server when the field changes in the client. For example,
	`on_change="onchange_shop_id(shop_id)"`. 
:relation:
	Used when a field is an id reference to another table. This is the name of
	the table to look in. Most commonly used with related and function field
	types.
:select: 
	Default value for the `select` attribute in the view. 1 means basic search,
	and 2 means advanced search.
