OpenERP Objects
===============

Introduction
----------------

.. This chapter is dedicated to detailed objects definition:
    all fields
    all objects
    inheritancies

All the ERP's pieces of data are accessible through "objects". As an example, there is a res.partner object to access the data concerning the partners, an account.invoice object for the data concerning the invoices, etc...

Please note that there is an object for every type of resource, and not an
object per resource. We have thus a res.partner object to manage all the
partners and not a *res.partner* object per partner. If we talk in "object
oriented" terms, we could also say that there is an object per level.

The direct consequences is that all the methods of objects have a common parameter: the "ids" parameter. This specifies on which resources (for example, on which partner) the method must be applied. Precisely, this parameter contains a list of resource ids on which the method must be applied.

For example, if we have two partners with the identifiers 1 and 5, and we want to call the res_partner method "send_email", we will write something like::

        res_partner.send_email(... , [1, 5], ...)

We will see the exact syntax of object method calls further in this document.

In the following section, we will see how to define a new object. Then, we will check out the different methods of doing this.

For developers:

* OpenERP "objects" are usually called classes in object oriented programming.
* A OpenERP "resource" is usually called an object in OO programming, instance of a class. 

It's a bit confusing when you try to program inside OpenERP, because the language used is Python, and Python is a fully object oriented language, and has objects and instances ...

Luckily, an OpenERP "resource" can be converted magically into a nice Python object using the "browse" class method (OpenERP object method). 


