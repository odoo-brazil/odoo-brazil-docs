
.. _yaml-serialization:

YAML Data Serialization
=======================

YAML is a **human-readable** data serialization format that takes concepts from
programming languages such as C, Perl, and **Python**, and ideas from **XML**
and the data format of electronic mail.
YAML stands for *YAML Ain't Markup Language* (yes, that's a recursive acronym).
YAML is available as a format for OpenERP data **as of OpenERP 6.0**, featuring
the following advantages:

    * User friendly format as an alternative to our current XML data format.
    * Same system to load data or tests, integrated in modules.
    * Built in OpenERP so that you can develop complex Python tests.
    * Simpler for non developers to write functional tests.

The following section compares an XML record with an equivalent YAML record.

First the XML Record using the current XML serialization format
(see :ref:`previous section <xml-serialization>`)

.. code-block:: xml

  <!--
      Resource: sale.order
  -->

  <record id="order" model="sale.order">
    <field name="shop_id" ref="shop"/>
    <field model="product.pricelist" name="pricelist_id" search="[]"/>
    <field name="user_id" ref="base.user_root"/>
    <field model="res.partner" name="partner_id" search="[]"/>
    <field model="res.partner.address" name="partner_invoice_id search="[]"/>
    <field model="res.partner.address" name="partner_shipping_id" search="[]"/>
    <field model="res.partner.address" name="partner_order_id" search="[]"/>
  </record>

  <!--
        Resource: sale.order.line
  -->

  <record id="line" model="sale.order.line">
    <field name="order_id" ref="order"/>
    <field name="name">New server config + material</field>
    <field name="price_unit">123</field>
  </record>

  <record id="line1" model="sale.order.line">
    <field name="order_id" ref="order"/>
    <field name="name">[PC1] Basic PC</field>
    <field name="price_unit">450</field>
  </record>

YAML Record
------------
::

    #<!--
    #       Resource: sale.order
    #   -->


    -
     !record {model: sale.order, id: sale_order_so4}:
       amount_total: 3263.0
       amount_untaxed: 3263.0
       create_date: '2010-04-06 10:45:14'
       date_order: '2010-04-06'
       invoice_quantity: order
       name: SO001
       order_line:
         - company_id: base.main_company
           name: New server config + material
           order_id: sale_order_so4
           price_unit: 123.0
         - company_id: base.main_company
           name: '[PC1] Basic PC'
           order_id: sale_order_so4
           price_unit: 450.0
       order_policy: manual
       partner_id: base.res_partner_agrolait
       partner_invoice_id: base.main_address
       partner_order_id: base.main_address
       partner_shipping_id: base.main_address
       picking_policy: direct
       pricelist_id: product.list0
       shop_id: sale.shop

YAML Tags
----------
data
^^^^
* **Tag**: data

* **Compulsory attributes**: None

* **Optional attributes**: noupdate \: 0 | 1

* **Child_tags**:

  - menuitem

  - record

  - workflow

  - delete

  - act_window

  - assert

  - report

  - function

  - ir_set


* **Example**:
  ::

    -
      !context
       noupdate: 0

record
^^^^^^^
* **Tag**: record

* **Compulsory attributes**:
                - model

* **Optional attributes**: noupdate \: 0 | 1

* **Child_tags**:
            - field

* **Optional attributes**:
                      - id

                      - forcreate

                      - context

* **Example**:
  ::

    -
      !record {model: sale.order, id: order}:
         name: "[PC1] Basic PC"
         amount_total: 3263.0
         type_ids:
           - project_tt_specification
           - project_tt_development
           - project_tt_testing
         order_line:
             - name: New server config
                order_id: sale_order_so4
             - name: '[PC1] Basic PC'
                order_id: sale_order_so4

field
^^^^^^

* **Tag**: field

* **Compulsory attributes**:
                - name

* **Optional attributes**:
                      - type

                      - ref

                      - eval

                      - domain

                      - search

                      - model

                      - use
* **Child_tags**:
            - text node

* **Example**:
  ::

    -price_unit: 450
    -product_id: product.product_product_pc1

workflow
^^^^^^^^^
* **Tag**: workflow

* **Compulsory attributes**:
                - model

                - action

* **Optional attributes**:
                 - uid

                 - ref

* **Child_tags**:
            - value

* **Example**:
  ::

   -
    !workflow {action: invoice_open, model: account.invoice}:
     - eval: "obj(ref('test_order_1')).invoice_ids[0].id"
       model: sale.order
     - model: account.account
       search: [('type', '=', 'cash')]

function
^^^^^^^^^
* **Tag**: function

* **Compulsory attributes**:
                - model

                - name


* **Optional attributes**:
                 - id

                 - eval

* **Child_tags**:
            - value

            - function

* **Example**:
  ::

   -
    !function {model: account.invoice, name: pay_and_reconcile}:
     -eval: "[obj(ref('test_order_1')).id]"
      model: sale.order

value
^^^^^^
* **Tag**: value

* **Compulsory attributes**: None

* **Optional attributes**:
                 - model

                 - search

                 - eval

* **Child_tags**: None

* **Example**:
  ::

     -eval: "[obj(ref('test_order_1')).id]"
      model: sale.order

menuitem
^^^^^^^^^
* **Tag**: menuitem

* **Compulsory attributes**: None

* **Optional attributes**:
                 - id

                 - name

                 - parent

                 - icon

                 - action

                 - string

                 - sequence

                 - groups

                 - type

                 - menu

* **Child_tags**: None

* **Example**:
  ::

     -
      !menuitem {sequence: 20, id: menu_administration,
       name: Administration,
       icon: terp-administration}

act_window
^^^^^^^^^^^
* **Tag**: act_window

* **Compulsory attributes**:
                - id

                - name

                - res_model

* **Optional attributes**:

                - domain

                - src_model

                - context

                - view

                - view_id

                - view_type

                - view_mode

                - multi

                - target

                - key2

                - groups


* **Child_tags**: None

* **Example**:
  ::

     -
       !act_window {target: new,
       res_model: wizard.ir.model.menu.create,
       id:act_menu_create, name: Create Menu}

report
^^^^^^^
* **Tag**: report

* **Compulsory attributes**:
                - string

                - model

                - name

* **Optional attributes**:

                - id

                - report

                - multi

                - menu

                - keyword

                - rml

                - sxw

                - xml

                - xsl

                - auto

                - header

                - attachment

                - attachment_use

                - groups

* **Child_tags**: None

* **Example**:
  ::

     -
       !report {string: Technical guide,
        auto: False, model: ir.module.module,
        id: ir_module_reference_print,
        rml: base/module/report/ir_module_reference.rml,
        name: ir.module.reference}

ir_set
^^^^^^
* **Tag**: ir_set

* **Compulsory attributes**: None

* **Optional attributes**: None

* **Child_tags**:
            - field

* **Example**:
  ::

   -
    !ir_set:
    args: "[]"
    name: account.seller.costs
    value: tax_seller

python
^^^^^^^
* **Tag**: Python

* **Compulsory attributes**:
            - model

* **Optional attributes**: None

* **Child_tags**: None

* **Example**:
  ::

   Python code

delete
^^^^^^^
* **Tag**: delete

* **Compulsory attributes**:
            - model

* **Optional attributes**:
                - id

                - search

* **Child_tags**: None

* **Example**:
  ::

   -
     !delete {model: ir.actions, search: "[(model,like,auction.)]"}

assert
^^^^^^
* **Tag**: assert

* **Compulsory attributes**:
            - model

* **Optional attributes**:
                - id

                - search

                - string

* **Child_tags**:
        - test

* **Example**:
  ::

   -
     !assert {model: sale.order,
      id: test_order, string: order in progress}:
        - state == "progress"

test
^^^^^
* **Tag**: test

* **Compulsory attributes**:
            - expr

* **Optional attributes**: None

* **Child_tags**:
        - text node

* **Example**::

    - picking_ids[0].state == "done"

url
^^^^
* **Tag**: url

* **Compulsory attributes**: -

* **Optional attributes**: -

* **Child_tags**: -

* **Example**: -

Writing YAML Tests
==================

.. note::

    Please see also section :ref:`yaml-testing-guidelines`


**Write manually**
    * Record CRUD
    * Workflow transition
    * Assertions (one expression like in XML)
    * Pure Python code

**Use base_module_record(er)**

    * Generate YAML file with record and workflow

    .. figure::  images/record_object.png
       :align: center

    * Update this YAML with assertions / Python code

.. warning:: Important

   As yaml is structured with indentation(like Python), each child tag(sub-tag) must be indented as compared to its parent tag.


Field Tag
-----------

* text
    + text with special characters at beginning or at end must be enclosed with double quotes.
        **Ex: name: "[PC1] Basic PC"**

* integer and float
    **Ex: price_unit: 450**
    **Ex: amount_total: 3263.0**

* boolean
    **active: 1**

* datetime
    **date_start: str(time.localtime()[0] - 1) + -08-07**

* selection
    + give the shortcut
        **Ex: title: M.**

* many2one
    + if its a reference to res_id, specify the res_id
        **Ex: user_id: base.user_root**


    + if its value is based on search criteria specify the model to search on and the criteria
        **Ex: object_id: !ref {model: ir.model, search: "[('model','=','crm.claim')]”}**

* one2many
    + start each record in one2many field on a new line with a space and a hyphen
        **Ex: order_line:**
        **name: New server config**
        **order_id: sale_order_so4**
        **......**

        **name: '[PC1] Basic PC'**
        **order_id: sale_order_so4**
        **......**

* many2many
    + start each record in many2many field with a space and a hyphen
        **Ex: type_ids:**
        **- project_tt_specification **
        **- project_tt_development**
        **- project_tt_testing**

Value tag
-----------
* if the value can be evaluated(like res_id is available), we write value tag as follows:
    **-**
    **!function {model: account.invoice, name: pay_and_reconcile}:**
    **- eval: "obj(ref('test_order_1')).amount_total"**
    **model: sale.order**

    This will fetch the 'amount_total' value of a 'sale.order' record with res_id 'test_order_1'

* If the value is to be searched on some model based on a criteria, we write value tag as follows:
    **-**
    **!function {model: account.invoice, name: pay_and_reconcile}:**
    **- model: account.account**
    **search: "[('type', '=', 'cash')]"**
    This will fetch all those account.account records whose type is equal to 'cash'

Test Tag
--------

* specify the test directly
    **Ex:  - picking_ids[0].state == "done"**
    **- state == "manual"**

comment
--------

**#<!-- Resource: sale.order -->**

Asserts and Python code
------------------------
To create an invoice, python code could be written as:

**-**
  **!python {model: account.invoice}: |**
     **self.action_move_create(cr, uid, [ref("invoice1")])**


The invoice must be in draft state:

**-**
  **!assert {model: account.invoice , id: invoice1, string: "the invoice is now in Draft state"}:**
     **- state == "draft"**

To test that all account are in a tree data structure, we write the below python code:

**-**
  **!python {model: account.account}:**
    **ids = self.search(cr, uid, [])**

    **accounts_list = self.read(cr, uid, ids['parent_id','parent_left','parent_right'])**

    **accounts = dict((x['id'], x) for x in accounts_list)**

    **log("Testing parent structure for %d accounts", len(accounts_list))**

    **for a in accounts_list:**
        **if a['parent_id']:**
            **assert a['parent_left']>accounts[a['parent_id'][0]]['parent_left']**

            **assert a['parent_right']<accounts[a['parent_id'][0]]['parent_right']**

        **assert a['parent_left']<a['parent_right']**

    **for a2 in accounts_list:**

        **assert not ((a2['parent_right']>a['parent_left'])and**
            **(a2['parent_left']<a['parent_left'])and**

            **(a2['parent_right']<a['parent_right']))**

            **if a2['parent_id']==a['id']:**
                **assert(a2['parent_left']>a['parent_left'])and(a2['parent_right']<a['parent_right'])**

Running tests
--------------
    * Save the file with '.yml' extension
    * Add the yaml file under 'demo_xml' in terp file
    * Run the server with '--log-level=test' option

