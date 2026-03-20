# How to apply G/L entries

## Step 1 — Open the worksheet

On the **General Ledger Entries** page, position your cursor on any entry belonging to the account you want to work with. Click **Apply Entries** (or press **Shift+F11**).

The **Apply G/L Entries** worksheet opens, showing all entries for that G/L account.

![New]()
> 📸 *Screenshot: Apply G/L Entries worksheet loaded with entries for a G/L account.*

## Step 2 — Mark the base entry

Select the entry you want to apply from (the "base entry") and press **F7** (or click **Set Applies-to ID**). Your user ID appears in the **Applies-to ID** column.

![New]()
> 📸 *Screenshot: Apply G/L Entries worksheet with one entry showing the Applies-to ID filled in.*

## Step 3 — Mark the matching entries

Move to one or more matching entries and press **F7** on each. All marked entries will share the same Applies-to ID.

**Rules:**
- All entries must belong to the same G/L account
- All entries must be **Open**
- An entry cannot be applied to itself

![New]()
> 📸 *Screenshot: Apply G/L Entries worksheet with both a debit and credit entry marked with the same Applies-to ID.*

## Step 4 — Post the application

Press **F9** (or click **Post Application**). Confirm the dialog.

The app validates the selection, then posts the application atomically — either everything succeeds or nothing is written.

![New]()
> 📸 *Screenshot: The confirmation dialog "Do you want to post the application?".*

## Step 5 — Verify the result

After posting:

- Applied entries show **Open = No** and **Remaining Amount = 0**
- The Applies-to ID is cleared
- If the amounts don't fully net to zero, the base entry stays open with the leftover as its new Remaining Amount (partial application)

![New]()
> 📸 *Screenshot: Apply G/L Entries worksheet after posting, showing closed entries.*

---

[← Previous: Getting started](GettingStarted.md) | [Next: How to undo an application →](HowToUndoAnApplication.md)
