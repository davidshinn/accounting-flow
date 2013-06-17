accounting-flow
===============

This is a html and javascript project that assists with documenting
and visualizing the accounting flow from model journal entries.

It relies heavily on [d3.js](http://d3js.org).

Features
--------
With limited input required for journal entry details

* Renders t-accounts
 * In financial statement location
 * Calculates t-account subtotal
 * Calculates financial statement account category change (e.g., change in assets)
* Provides mouseover highlight effects to assist in visualizing relationships between
  the journal entries and t-accounts
 * Hovering over the t-account will highlight relating journal lines
 * Hovering over a t-account row will highlight the related journal line and vice versa
 * Hovering over the Journal Line Header:
  * will highlight all t-account entries relating to the journal entry
  * provide an extended tooltip description of the journal entry
* Automatically labels each journal line and related t-account entry alphabetically
  (e.g., "(A)") for readability after printing

Usage
-----

###Journal Line Details

Add journal entry details between:

    <pre id="csvdata">
    je_label,account_type,account,dr_cr,amount

and

    </pre>

in a comma separated format.  For example

    Buy Inventory,A,Inventory,dr,300

adds a journal line for a journal entry labeled **Buy Inventory**, that debits (**dr**)
an asset account (**A**) called **Inventory** for **300**

* je_label: Unique text identifying the distinct journal entry,
  must be the same for journal lines in the same journal entry
* account_type:
 * A: Assets
 * L: Liabilities
 * OE: Owners' Equity
 * R: Revenue
 * C: Cost of Revenue
 * E: Expenses
* account: Text identifying the account affected by the journal line
* dr_cr:
 * dr: Debit
 * cr: Credit
* amount: Plain number format, no commas, no decimals (e.g., 100)

###Journal extended description
Add journal entry header extended description between:

    <pre id="je_header">
    je_label,title

and

    </pre>

in a comma separated format:

* je_label: Unique text identifying the distinct journal entry
* title: Extended free text that shows up as a tool tip after rendering
