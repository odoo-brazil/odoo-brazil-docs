Events
======

On Change
------------

The on_change attribute defines a method that is called when the content of a view field has changed.

This method takes at least arguments: cr, uid, ids, which are the three classical arguments and also the context dictionary. You can add parameters to the method. They must correspond to other fields defined in the view, and must also be defined in the XML with fields defined this way::

        <field name="name_of_field" on_change="name_of_method(other_field'_1_', ..., other_field'_n_')"/> 

The example below is from the sale order view.

You can use the 'context' keyword to access data in the context that can be used as params of the function.::

        <field name="shop_id" on_change="onchange_shop_id(shop_id)"/>

.. code-block:: python

        def onchange_shop_id(self, cr, uid, ids, shop_id):

            v={} 
            if shop_id:

                shop=self.pool.get('sale.shop').browse(cr,uid,shop_id) 
                v['project_id']=shop.project_id.id 
                if shop.pricelist_id.id:

                    v['pricelist_id']=shop.pricelist_id.id 

                v['payment_default_id']=shop.payment_default_id.id 

            return {'value':v} 


When editing the shop_id form field, the onchange_shop_id method of the sale_order object is called and returns a dictionary where the 'value' key contains a dictionary of the new value to use in the 'project_id', 'pricelist_id' and 'payment_default_id' fields.

Note that it is possible to change more than just the values of
fields. For example, it is possible to change the value of some fields
and the domain of other fields by returning a value of the form:
return {'domain': d, 'value': value}

:returns: a dictionary with any mix of the following keys:

    ``domain``
      A mapping of ``{field: domain}``.

      The returned domains should be set on the fields instead of the
      default ones.

    ``value``
      A mapping of ``{field: value}}``, the values will be set on the
      corresponding fields and may trigger new onchanges or attrs
      changes

    ``warning`` A dict with the keys ``title`` and ``message``. Both
      are mandatory. Indicate that an error message should be
      displayed to the user.
