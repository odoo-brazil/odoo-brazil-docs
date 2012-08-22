
Financial Analysis
==================

Various reports designed for financial analysis are based on the analytic accounts. Most of those
are available directly from the tree of accounts or from the form view of the account.

Analysis per Account
--------------------

From an `Analytic Account` form, click on one of the :guilabel:`REPORTS` buttons to select a report.
OpenERP provides the following financial analyses from the analytic accounts (and maybe more,
depending on the additional installed modules):

*  :guilabel:`Cost Ledger`,

*  :guilabel:`Cost Ledger (quantities only)`.

*  :guilabel:`Inverted Analytic Balance`,

*  :guilabel:`Analytic Balance`,

.. index::
   pair: cost ledger; analytic

The Cost Ledger
^^^^^^^^^^^^^^^

The cost ledger provides all of the
detailed entries for the selected accounts. It enables you to make a detailed analysis of each operation carried
out on one or several projects.

.. figure::  images/analytic_cost_ledger.png
   :scale: 65
   :align: center

   *The analytic cost ledger gives a detailed history of the entries in an analytic account*

The Cost Ledger (Quantities Only)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This report gives the detail of entries for an analytic account and a list of selected journals.
Only quantities are reported for this analysis, not costs and revenues.

.. figure::  images/analytic_cost_ledger_quantity.png
   :scale: 65
   :align: center

   *The cost ledger (quantities only) gives a history of an analytic account*

The report is often used to print the number of hours worked on a project, without exposing the
costs and revenues. So you can show it to a client as a record of the hours worked on a particular
project.

To restrict the report to hours worked, without including sales and purchases, select only the
services journal for printing.

.. tip:: Multiple Printing

	To print several analytic accounts at once, you can make a multiple selection on the different
	accounts in the tree of accounts.
	Then click on the appropriate :guilabel:`Report` in the toolbar (in the web client), or
	select one of the :guilabel:`Print` reports (in the GTK client), to export the whole selection into a
	single PDF document.

.. index::
   pair: balance; analytic

Inverted Analytic Balance
^^^^^^^^^^^^^^^^^^^^^^^^^

The inverted analytic balance provides a summary report relating general accounts and
analytic accounts. This report shows the balances of the general accounts
broken down by the selected analytic accounts for a selected period.

.. figure::  images/analytic_balance_inverse.png
   :scale: 65
   :align: center

   *The inverted analytic balance shows a breakdown of operations by analytic account (project)*

This enables you to analyze your costs by general account. For example, if you examine your general
account for staff salaries, you can obtain all your salary costs broken down by the different
analytic (or project) accounts.

Analytic Balance
^^^^^^^^^^^^^^^^

.. figure::  images/analytic_balance.png
   :scale: 65
   :align: center

   *The analytic balance shows a breakdown of each project by operation in the financial accounts*

The analytic balance is a summary report that relates the analytic accounts to the general accounts. It
shows the balances of the analytic accounts broken down by general account for a selected period.

This report is useful for analyzing the profitability of projects, giving you the profitability of
a project for the different operations that you used to carry out the project.

.. index::
   single: multi-company

.. tip::  Multi-company

	In a multi-company environment, each company can have its own general chart of accounts on the same
	database.
	The two general charts of accounts are independent, but can be linked in a third chart using a
	view account to do the consolidation.

	If the different companies collaborate on joint projects, they may all share the same analytic chart
	of accounts.
	In this environment, the cross-related reports like the balance and inverted balance are extremely
	useful, because
	they enable you to make an analysis per company by linking up to the general accounts.

Analytic Entries Analysis
^^^^^^^^^^^^^^^^^^^^^^^^^

You can have the statistical analysis on all analytic entries from the menu
:menuselection:`Accounting --> Reporting --> Statistic Reports --> Analytic Entries Analysis`.

.. figure::  images/analytic_entries_analysis.png
   :scale: 75
   :align: center

   *Statistical report for analytic entries*


Key Indicators
--------------

.. index::
   single: module; account_analytic_analysis

If you use analytic accounts with a structure of accounts by project client, you should install the
:mod:`account_analytic_analysis` module. This module adds three new tabs to the analytic account
form:

* management indicators in the :guilabel:`Analysis summary` tab,

* monthly statistics in the :guilabel:`Stats by month` tab,

* statistics on each user in the :guilabel:`Stats by user` tab.

.. _fig-mgtindic:

.. figure::  images/account_analytic_analysis.png
   :scale: 75
   :align: center

   *Management indicators for an analytic account*

The figure :ref:`fig-mgtindic` shows all of the management indicators.

These indicators enable you to quickly see such important information as:

* project profitability,

* whether you can still invoice any services to the client, or not,

* the amount of services to invoice,

* the different margin figures.

.. figure::  images/account_analytic_analysis_month.png
   :scale: 75
   :align: center

   *Breakdown of monthly costs for an analytic account*

The real revenue is given by the amount invoiced to the client. The theoretical revenue is given by
the sale price of different project costs which could be invoiced to the client. These give
different margin figures.

For example, in the case of a fixed price project contract, the real sale price at the end of the
project will be equal to the contract negotiated with the client. The theoretical price gives the
amount that would have been invoiced if you had charged for all the time worked.

To give project managers a direct view of their different projects, the
:mod:`account_analytic_analysis` module creates new menus in the Project management module in
:menuselection:`Project --> Billing --> Overpassed Accounts`.

.. figure::  images/account_analytic_project_menu.png
   :scale: 65
   :align: center

   *Analytic accounts in Project Management*

These different menus give quick views that are useful for live projects. For each project, you
can check if there are uninvoiced services, see the last invoice date and the last uninvoiced
service date, and get reports on the amounts received and those planned. So project managers have
all the information necessary to manage their project, shown in a single page.

In the following chapters you will see how project managers can use this information to carry out
the various operations needed to manage the project, such as automatic invoicing, project
planning, keeping customers up-to-date, and budgeting for resources.

.. index::
   single: module; account_budget

.. note:: Analytic Budgets

	Analytic budgets can be budgeted in the :mod:`account_budget` module. They offer:

	* forecasting projects in the medium term,

	* controlling project costs,

	* comparisons with general accounts.

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

