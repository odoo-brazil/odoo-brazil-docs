Introduction
============

OpenERP uses a `three-tier architecture
<http://en.wikipedia.org/wiki/Multitier_architecture#Three-tier_architecture>`_.
The application tier itself is written as a core and multiple additional
modules that can be installed or not to create a particular configuration of
OpenERP.

The core of OpenERP and its different modules are written in `Python
<http://python.org/>`_. The functionality of a module is exposed through
XML-RPC (and/or NET-RPC depending on the server's configuration). Modules also
typically make use of OpenERP ORM to persist their data in a relational
database (PostgreSQL). Modules can insert data in the database during
installation by providing XML (or CSV or YML) files.

Although  modules are a simple way to structure a complex application,
OpenERP modules also extend the system. Modules are
also called addons (they could also have been called plugins).

In a typical configuration of OpenERP, the following modules can be found:

    * base: the most basic module; it is always installed and can be thought
      as being part of the core of OpenERP. It defines ``ir.property``,
      ``res.company``, ``res.request``, ``res.currency``, ``res.users``,
      ``res.partner``, and so on.
    * crm: Customer & Supplier Relationship management.
    * sale: Sales management.
    * mrp: Manufacturing Resource Planning. 

By using Python, XML files, and relying on OpenERP's ORM and its extensibility
mechanisms, new modules can be written easily and quickly. OpenERP's open
source nature and its numerous modules also provide a lot of examples for any
new development.

