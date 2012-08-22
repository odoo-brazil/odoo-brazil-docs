
.. index::
   single: journal; configuring

Journals
========

All your accounting entries must appear in an accounting journal. So you must, at a minimum, create
a Sales Journal for customer invoices, a Purchase Journal for supplier invoices and a Cash Journal
for cash and bank transactions.

Configuring a Journal
---------------------

To view, edit or create new journals use the menu :menuselection:`Accounting -->
Configuration --> Financial Accounting --> Journals --> Journals`.

.. figure::  images/account_journal_form.png
   :scale: 75
   :align: center

   *Definition of an accounting journal*

You have to associate a view with each journal. The journal view indicates the fields that must be
visible and required to enter accounting data in that journal. The view determines both the order of
the fields and the properties of each field. For example, the field :guilabel:`Account Number` must
appear when entering data in the bank journal but not in the other journals.

Before creating a new view for a journal, check that there is nothing similar already defined for
another journal. You should only create a new view for new types of journals.

.. note:: Customizing Views

	You will often have to edit a journal view.
	For example, for a journal in a foreign currency you add a field for the currency, and this currency
	must be in the journal view.

	Conversely, to simplify data entry, the journal view for the bank is quite different from one of the
	invoicing journals.

You can create a sequence for each journal. This sequence gives the automatic numbering for
accounting entries. Or several journals can use the same sequence if you want to define one for them
all.

The credit and debit account by default permit the automatic generation of counterpart entries when
you are entering data in the journal quickly. For example, in a bank journal you should put an
associated bank account for default matching credits and debits, so that you do not have to create
counterparts for each transaction manually.

A journal can be marked as being centralized. When you do this, the counterpart entries will not be
owned by each entry, but globally for the given journal and period. You will then have a credit line
and a debit line centralized for each entry in one of these journals, meaning that both credit and
debit appear on the same line.

Controls and Tips for Data Entry
--------------------------------

You can carry out two types of control on journals in OpenERP – controls over the financial
accounts and access controls for groups of users. In addition to these controls, you can also apply
all of the rights management detailed in :ref:`ch-config`.

To avoid mistakes while entering accounts data, you can place conditions in the general accounts
about who can use a given account. To do this, you must list all the accounts or valid account types
in the second tab, :guilabel:`Entry Controls`. If you have not added any accounts there, OpenERP applies no
restriction on data entry in the accounts or journals. If you list accounts and the types of accounts
that can be used in a journal, OpenERP prevents you from using any account not in that list. This
verification step starts from the moment you save the entry.

This functionality is useful for limiting possible data entry errors. Also, in a bank journal, it is
possible to restrict the accounts that can be linked to a bank to classes 1 to 5. Using this, you would
help prevent the user from making any false entries in the journal.

.. tip:: Control of Data Entry

	In accounting it is not a good idea to allow a data entry directly from bank account A to bank
	account B.
	If you enter a transaction from bank A to bank B, the transaction will be accounted for twice.

	To prevent this problem, pass the transaction through intermediate account C.
	At the time of data entry, the system checks the type of account that is accepted in the bank
	journal:
	only accounts that are not of type ``Bank`` are accepted.

	If your accountant defines this control properly, non-accounting users are prevented from
	transferring payment from one bank to another, reducing your risks.

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
