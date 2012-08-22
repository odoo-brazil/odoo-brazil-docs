
Periods and Financial Years
===========================

.. note:: Periods and Fiscal Years

        A fiscal year (or financial year) corresponds to twelve months for a company.
        In many countries, the fiscal year corresponds to a calendar year. That is not the case in
        others.

        The fiscal year is divided into monthly or three-monthly accounting periods.

OpenERP's management of the fiscal year is flexible enough to enable you to work on several years
at the same time. This gives you several advantages, such as creating three-year budgets, and
statements straddling several calendar years.

.. index:: period
.. index:: fiscal year

.. _financialyear:

Defining a Period or a Financial Year
-------------------------------------

To define your fiscal year, use the menu :menuselection:`Accounting --> Configuration -->
Financial Accounting --> Periods --> Fiscal Year`. You can create several years in advance to define long-term budgets.

.. figure::  images/account_period.png
   :scale: 75
   :align: center

   *Defining a financial year and periods*

First enter the date of the first day of your fiscal year and the last day. Then to create the
periods, click one of the two buttons at the bottom depending on whether you want to create twelve
1-month or four 3-month periods:

*  :guilabel:`Create Monthly Periods` ,

*  :guilabel:`Create 3 Months Periods` .

Closing a Financial Year
------------------------

To close a financial year, use the menu :menuselection:`Accounting--> Periodical Processing --> End of Period --> Close a Fiscal Year`.
A wizard opens asking you for the essential information it needs
to close the following year.

When the year is closed, you can no longer create or modify any financial transactions in that year.
So you should always make a backup of the database before closing the fiscal year. Closing a year
is not obligatory, and you could easily do that sometime in the following year, when your accounts are
finally sent to the statutory authorities, and no further modifications are permitted.

.. figure::  images/account_fy_close.png
   :scale: 75
   :align: center

   *Closing a financial year*

It is also possible to close an accounting period. You could, for example, close a monthly period when
a tax declaration has been made. When a period is closed, you cannot modify any of the entries in that
period. To close an accounting period, use the menu :menuselection:`Accounting--> Periodical Processing --> End of Period --> Close a Period`.

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
