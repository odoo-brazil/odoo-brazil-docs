Technical Architecture
======================

Overview
--------

OpenERP is a `multitenant <http://en.wikipedia.org/wiki/Multitenancy>`_,
`three-tier architecture
<http://en.wikipedia.org/wiki/Multitier_architecture#Three-tier_architecture>`_.
The application tier itself is written as a core, multiple additional
modules can be installed to create a particular configuration of
OpenERP.

The core of OpenERP and its modules are written in `Python
<http://python.org/>`_. The functionality of a module is exposed through
XML-RPC (and/or NET-RPC depending on the server's configuration)[#]. Modules
typically make use of OpenERP's ORM to persist their data in a relational
database (PostgreSQL). Modules can insert data in the database during
installation by providing XML, CSV, or YML files.

.. [#] JSON-RPC is planned for OpenERP v6.1.

The OpenERP server
++++++++++++++++++

OpenERP provides an application server on which specific business applications
can be built. It is also a complete development framework, offering a range of
features to write those applications. The salient features are a flexible ORM,
a MVC architecture, extensible data models and views, different report engines,
all tied together in a coherent, network-accessible framework.

From a developer perspective, the server acts both as a library which brings
the above benefits while hiding the low-level, nitty-gritty details, and as a
simple way to install, configure and run the written applications.

Modules
+++++++

By itself, the OpenERP server is not very useful. For any enterprise, the value
of OpenERP lies in its different modules. It is the role of the modules to
implement any business needs. The server is only the necessary machinery to run
the modules. A lot of modules already exist. Any official OpenERP release
includes about 170 of them, and hundreds of modules are available through the
community. Examples of modules are Account, CRM, HR, Marketing, MRP, Sale, etc.

A module is usually composed of data models, together with some initial data,
views definitions (i.e. how data from specific data models should be displayed
to the user), wizards (specialized screens to help the user for specific
interactions), workflows definitions, and reports.

Clients
+++++++

Clients can communicate with an OpenERP server using XML-RPC. A custom, faster
protocol called NET-RPC is also provided but will shortly disappear, replaced
by JSON-RPC. XML-RPC, as JSON-RPC in the future, makes it possible to write
clients for OpenERP in a variety of programming languages. OpenERP S.A.
develops two different clients: a desktop client, written with the widely used
`GTK+ <http://www.gtk.org/>`_ graphical toolkit, and a web client that should
run in any modern web browser.

As the logic of OpenERP should entirely reside on the server, the client is
conceptually very simple; it issues a request to the server and display the result
(e.g. a list of customers) in different manners (as forms, lists, calendars,
...). Upon user actions, it will send modified data to the server.


Architecture
------------


.. figure::  images/client_server.png
   :scale: 85
   :align: center


Relational database server and ORM
++++++++++++++++++++++++++++++++++

The data tier of OpenERP is provided by a PostgreSQL relational database. While
direct SQL queries can be executed from OpenERP modules, most database access
to the relational database is done through the `Object-Relational Mapping
<http://en.wikipedia.org/wiki/Object-relational_mapping>`_.

The ORM is one of the salient features mentioned above. The data models are
described in Python and OpenERP creates the underlying database tables. All the
benefits of RDBMS (unique constraints, relational integrity, efficient
querying, ...) are used when possible and completed by Python flexibility. For
instance, arbitrary constraints written in Python can be added to any model.
Different modular extensibility mechanisms are also afforded by OpenERP[#].

.. [#] It is important to understand the ORM responsibility before attempting to by-pass it and access directly the underlying database via raw SQL queries.  When using the ORM, OpenERP can make sure the data remains free of any corruption.  For instance, a module can react to data creation in a particular table. This reaction can only happen if the ORM is used to create that data.

Models
++++++

To define data models and otherwise pursue any work with the associated data,
OpenERP as many ORMs uses the concept of 'model'. A model is the authoritative
specification of how some data are structured, constrained, and manipulated. In
practice, a model is written as a Python class. The class encapsulates anything
there is to know about the model: the different fields composing the model,
default values to be used when creating new records, constraints, and so on. It
also holds the dynamic aspect of the data it controls: methods on the class can
be written to implement any business needs (for instance, what to do upon user
action, or upon workflow transitions).

There are two different models. One is simply called 'model', and the second is
called 'transient model'. The two models provide the same capabilities with a
single difference: transient models are automatically cleared from the
database (they can be cleaned when some limit on the number of records is
reached, or when they are untouched for some time).

To describe the data model per se, OpenERP offers a range of different kind of
fields. There are basic fields such as integer, or text fields. There are
relational fields to implement one-to-many, many-to-one, and many-to-many
relationships. There are so-called function fields, which are dynamically
computed and are not necessarily available in database, and more.

Access to data is controlled by OpenERP and configured by different mechanisms.
This ensures that different users can have read and/or write access to only the
relevant data. Access can be controlled with respect to user groups and rules
based on the value of the data themselves.

Modules
+++++++

OpenERP supports a modular approach both from a development perspective and a
deployment point of view. In essence, a module groups everything related to a
single concern in one meaningful entity. It is comprised of models, views,
workflows, and wizards.

Services and WSGI
+++++++++++++++++

Everything in OpenERP, and models methods in particular, are exposed via the
network and a security layer. Access to the data model is in fact a 'service'
and it is possible to expose new services. For instance, a WebDAV service and a
FTP service are available.

While not mandatory, the services can make use of the `WSGI
<http://en.wikipedia.org/wiki/Web_Server_Gateway_Interface>`_ stack.
WSGI is a standard solution in the Python ecosystem to write HTTP servers,
applications, and middleware which can be used in a mix-and-match fashion.
By using WSGI, it is possible to run OpenERP in any WSGI-compliant server, but
also to use OpenERP to host a WSGI application.

A striking example of this possibility is the OpenERP Web project. OpenERP Web
is the server-side counter part to the web clients. It is OpenERP Web which
provides the web pages to the browser and manages web sessions. OpenERP Web is
a WSGI-compliant application. As such, it can be run as a stand-alone HTTP
server or embedded inside OpenERP.

XML-RPC, JSON-RPC
+++++++++++++++++

The access to the models makes also use of the WSGI stack. This can be done
using the XML-RPC protocol, and JSON-RPC will be added soon.


Explanation of modules:

**Server - Base distribution**

We use a distributed communication mechanism inside the OpenERP server. Our engine supports most commonly distributed patterns: request/reply, publish/subscribe, monitoring, triggers/callback, ...

Different business objects can be in different computers or the same objects can be on multiple computers to perform load-balancing.

**Server - Object Relational Mapping (ORM)**

This layer provides additional object functionality on top of PostgreSQL:

    * Consistency: powerful validity checks,
    * Work with objects (methods, references, ...)
    * Row-level security (per user/group/role)
    * Complex actions on a group of resources
    * Inheritance 

**Server - Web-Services**

The web-service module offer a common interface for all web-services

    * SOAP
    * XML-RPC
    * NET-RPC 

Business objects can also be accessed via the distributed object mechanism. They can all be modified via the client interface with contextual views.

**Server - Workflow Engine**

Workflows are graphs represented by business objects that describe the dynamics of the company. Workflows are also used to track processes that evolve over time.

An example of workflow used in OpenERP:

A sales order generates an invoice and a shipping order

**Server - Report Engine**

Reports in OpenERP can be rendered in different ways:

    * Custom reports: those reports can be directly created via the client interface, no programming required. Those reports are represented by business objects (ir.report.custom)
    * High quality personalized reports using openreport: no programming required but you have to write 2 small XML files:

          - a template which indicates the data you plan to report
          - an XSL:RML stylesheet 
    * Hard coded reports
    * OpenOffice Writer templates 

Nearly all reports are produced in PDF.

**Server - Business Objects**

Almost everything is a business object in OpenERP, they describe all data of the program (workflows, invoices, users, customized reports, ...). Business objects are described using the ORM module. They are persistent and can have multiple views (described by the user or automatically calculated).

Business objects are structured in the /module directory.

**Client - Wizards**

Wizards are graphs of actions/windows that the user can perform during a session.

**Client - Widgets**

Widgets are probably, although the origin of the term seems to be very difficult to trace, "WIndow gaDGETS" in the IT world, which mean they are gadgets before anything, which implement elementary features through a portable visual tool.

All common widgets are supported:

    * entries
    * textboxes
    * floating point numbers
    * dates (with calendar)
    * checkboxes
    * ... 

And also all special widgets:

    * buttons that call actions
    * references widgets

          - one2one

          - many2one

          - many2many

          - one2many in list

          - ... 

Widget have different appearances in different views. For example, the date widget in the search dialog represents two normal dates for a range of date (from...to...).

Some widgets may have different representations depending on the context. For example, the one2many widget can be represented as a form with multiple pages or a multi-columns list.

Events on the widgets module are processed with a callback mechanism. A callback mechanism is a process whereby an element defines the type of events he can handle and which methods should be called when this event is triggered. Once the event is triggered, the system knows that the event is bound to a specific method, and calls that method back. Hence callback. 
