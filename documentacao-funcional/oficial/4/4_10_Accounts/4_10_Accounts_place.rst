
.. index::
   single: analytic; accounts

Putting Analytic Accounts in Place
==================================

For the initial setup of good analytic accounts you should:

* set up the chart of accounts,

* create the different journals.

Setting up the Chart of Accounts
--------------------------------

Start by choosing the most suitable analytic representation for your company before entering it into
OpenERP. To create the different analytic accounts, use the menu :menuselection:`Accounting
--> Configuration --> Analytic Accounting --> Analytic Accounts` and click the `New` button.

.. figure::  images/account_analytic_form.png
   :scale: 75
   :align: center

   *Setting up an analytic account*

To create an analytic account, you have to complete the main fields:

* the :guilabel:`Account Name`,

* the :guilabel:`Account Code` : used as a shortcut for selecting the account,

* the :guilabel:`Account Type` : just like general accounts, the \ ``View``\   type is used for
  virtual accounts which are used only to create a hierarchical structure and for subtotals, and not
  to store accounting entries,

* the :guilabel:`Parent Analytic Account` : defines the hierarchy between the accounts.

If the project is for a limited time you can define a start and end date here. The :guilabel:`State`
field is used to indicate whether the project is running (\ ``Open``\ ), waiting for information
from the client (\ ``Pending``\ ), \ ``Draft``\   or \ ``Closed``\  .

Finally, if the analytic account is a client project you can complete the fields about the partner,
which you would need so that you can invoice the partner:

* the :guilabel:`Partner`,

* a :guilabel:`Sale Pricelist`, which shows how services linked to the project should be charged,

* a :guilabel:`Max. Invoice Price`, showing the maximum invoice price regardless of actual
  overspend,

* a :guilabel:`Maximum Quantity`, for contracts with a fixed limit of hours to use,

* an :guilabel:`Invoicing Rate per Journal` field, which defines an invoicing rate and whether the project
  should be invoiced automatically from the services represented by the costs in the analytic account.

.. index::
   single: invoicing

.. tip:: Invoicing

	You have several methods available to you in OpenERP for automated invoicing:

	* Service companies usually use invoicing from purchase orders, analytic accounts or 
	  project management tasks.

	* Manufacturing and trading companies more often use invoicing from deliveries or customer purchase
	  orders.

Once you have defined the different analytic accounts, you can view your chart through the menu
:menuselection:`Accounting --> Charts --> Chart of Analytic Accounts`.

.. figure::  images/account_analytic_chart.png
   :scale: 65
   :align: center

   *Example of an analytic chart for projects*

.. index::
   single: module; hr_timesheet_invoice
   single: module; account_analytic_analysis

.. tip:: Setting up an Analytic Account

	The setup screen for an analytic account can vary greatly depending on the modules installed in
	your database.
	For example, you will see information about recharging services only if you have the module
	:mod:`hr_timesheet_invoice` installed.

	Some of these modules add helpful management statistics to the analytic account.
	The most useful is probably the module :mod:`account_analytic_analysis`,
	which adds such information as indicators about your margins, invoicing amounts, and latest service
	dates and invoice dates.

Creating Journals
-----------------

Once the analytic chart has been created for your company you have to create the different journals.
These enable you to categorize the different accounting entries by their type:

* services,

* expense reimbursements,

* purchases of materials,

* miscellaneous expenditure,

* sales,

* situation entries (special situations, such as installation of the software).

.. index::
   single: journal; minimal journals

.. note::  Minimal Journals

	At a minimum, you have to create one analytic journal for Sales and one for Purchases.
	If you do not create these two, OpenERP will not validate invoices linked to an analytic account,
	because it would not be able to create an analytic accounting entry automatically.

.. figure::  images/account_analytic_journal.png
   :scale: 75
   :align: center

   *Creating an analytic journal*

To define your analytic journals, use the menu :menuselection:`Accounting -->
Configuration --> Analytic Accounting --> Analytic Journals` then click :guilabel:`New`.

It is easy to create an analytic journal. Just give it a :guilabel:`Journal Name`, a :guilabel:`Journal Code` and a :guilabel:`Type`. The
types available are:

* \ ``Sales``\  , for sales to customers and for credit notes,

* \ ``Purchases``\  , for purchases and miscellaneous expenses,

* \ ``Cash``\  , for financial entries,

* \ ``Situation``\  , to adjust accounts when starting an activity, or at the end of the financial
  year,

* \ ``General``\  , for all other entries.

The type of journal enables the software to automatically select the analytic journal based on the
nature of the operation. For example, if you enter an invoice for a customer, OpenERP will
automatically search for an analytic journal of type \ ``Sales``\  .

Working with Analytic Levels
----------------------------

You can work with analytic levels using OpenERP by installing :mod:`account_analytic_default` module.

It allows you to automatically select analytic accounts based on some criteria:

* Product
* Partner
* User
* Company
* Date

You can configure these criteria using the menu :menuselection:`Accounting -->
Configuration --> Analytic Accounting --> Analytic Defaults` and click the `New` button.

.. figure::  images/account_analytic_default.png
   :scale: 75
   :align: center

   *Specify criteria to select analytic account automatically*

.. Copyright © Open Object Press. All rights reserved.

.. You may take electronic copy of this publication and distribute it if you don't
.. change the content. You can also print a copy to be read by yourself only.

.. We have contracts with different publishers in different countries to sell and
.. distribute paper or electronic based versions of this book (translated or not)
.. in bookstores. This helps to distribute and promote the OpenERP product. It
.. also helps us to create incentives to pay contributors and authors using author
.. rights of these sales.

.. Due to this, grants to translate, modify or sell this book are strictly
.. forbidden, unless Tiny SPRL (representing Open Object Press) gives you a
.. written authorisation for this.

.. Many of the designations used by manufacturers and suppliers to distinguish their
.. products are claimed as trademarks. Where those designations appear in this book,
.. and Open Object Press was aware of a trademark claim, the designations have been
.. printed in initial capitals.

.. While every precaution has been taken in the preparation of this book, the publisher
.. and the authors assume no responsibility for errors or omissions, or for damages
.. resulting from the use of the information contained herein.

.. Published by Open Object Press, Grand Rosière, Belgium

