ORM methods
===========

Keeping the context in ORM methods
----------------------------------

In OpenObject, the context holds very important data such as the language in
which a document must be written, whether function field needs updating or not,
etc.

When calling an ORM method, you will probably already have a context - for
example the framework will provide you with one as a parameter of almost 
every method.
If you do have a context, it is very important that you always pass it through
to every single method you call.

This rule also applies to writing ORM methods. You should expect to receive a
context as parameter, and always pass it through to every other method you call.. 

ORM methods
-----------

.. autoclass:: osv.osv.osv
   :members:
   :inherited-members:
   :show-inheritance:

