# Apply G/L Entries — Quick Reference Manual

> **Audience**: End users and support staff  
> **App version**: 27.4+  
> **Applies to**: Microsoft Dynamics 365 Business Central (Essentials & Premium, all country versions)

---

## What does Apply G/L Entries do?

Apply G/L Entries lets you match debit and credit entries on the same G/L account — just like you can already do for customer, vendor, and bank entries in standard Business Central. This gives you real-time visibility into which amounts are settled and which are still outstanding on any G/L account.

---

## Getting started

### Installation

Install the app from **Microsoft AppSource** or via **Extension Management** in Business Central. No configuration is required — the app is ready to use immediately.

On first install, the app initializes all existing G/L entries as **Open** with **Remaining Amount** equal to their original **Amount**. This is a one-time process.

>![New](https://github.com/bydynamics/AL-ApplyGLEntries-Support/blob/main/Assets/ScreenshotExtensionManagementpageshowingtheinstalledApplyGLEntriesextension.png)
> 📸 *Screenshot: Extension Management page showing the installed "Apply G/L Entries" extension.*
   


### New fields on General Ledger Entries

After installation, three new columns are available on the **General Ledger Entries** page (Page 20):

| Column | Description |
|---|---|
| **Open** | `Yes` if the entry is available for application; `No` if fully applied |
| **Remaining Amount** | The amount still available for application |
| **Applied Amount** | The total amount already applied |

> 📸 *Screenshot: General Ledger Entries page showing the Open, Remaining Amount, and Applied Amount columns.*

### New actions on General Ledger Entries

| Action | Shortcut | Description |
|---|---|---|
| **Apply Entries** | Shift+F11 | Opens the application worksheet for the selected G/L account |
| **Applied Entries** | — | Shows the application history for the selected entry |
| **Migration Log** | — | Shows the NL data migration log (if applicable) |

> 📸 *Screenshot: General Ledger Entries page with the "Application" action group visible in the action bar.*

---
[back](../README.md)
[next](../Scenarios/CopyDocument.md)

## How to apply G/L entries

### Step 1 — Open the worksheet

On the **General Ledger Entries** page, position your cursor on any entry belonging to the account you want to work with. Click **Apply Entries** (or press **Shift+F11**).

The **Apply G/L Entries** worksheet opens, showing all entries for that G/L account.

> 📸 *Screenshot: Apply G/L Entries worksheet loaded with entries for a G/L account.*

### Step 2 — Mark the base entry

Select the entry you want to apply from (the "base entry") and press **F7** (or click **Set Applies-to ID**). Your user ID appears in the **Applies-to ID** column.

> 📸 *Screenshot: Apply G/L Entries worksheet with one entry showing the Applies-to ID filled in.*

### Step 3 — Mark the matching entries

Move to one or more matching entries and press **F7** on each. All marked entries will share the same Applies-to ID.

**Rules:**
- All entries must belong to the same G/L account
- All entries must be **Open**
- An entry cannot be applied to itself

> 📸 *Screenshot: Apply G/L Entries worksheet with both a debit and credit entry marked with the same Applies-to ID.*

### Step 4 — Post the application

Press **F9** (or click **Post Application**). Confirm the dialog.

The app validates the selection, then posts the application atomically — either everything succeeds or nothing is written.

> 📸 *Screenshot: The confirmation dialog "Do you want to post the application?".*

### Step 5 — Verify the result

After posting:

- Applied entries show **Open = No** and **Remaining Amount = 0**
- The Applies-to ID is cleared
- If the amounts don't fully net to zero, the base entry stays open with the leftover as its new Remaining Amount (partial application)

> 📸 *Screenshot: Apply G/L Entries worksheet after posting, showing closed entries.*

---

## How to undo an application

### Step 1 — Open Applied Entries

From either the **General Ledger Entries** page or the **Apply G/L Entries** worksheet, click **Applied Entries** for the entry you want to reverse.

> 📸 *Screenshot: GL Entry App. Entries page showing application history records.*

### Step 2 — Undo

Select the application record and click **Undo Application**.

The app:
1. Marks the original application records as **Reversed** (nothing is deleted)
2. Restores the **Remaining Amount** and **Open** status on both entries
3. Records the reversal date for audit purposes

> 📸 *Screenshot: GL Entry App. Entries page with the Undo Application action highlighted.*

### Step 3 — Verify

The entries are back to **Open = Yes** with their original remaining amounts. The audit trail in Applied Entries shows both the original application and the reversal.

> 📸 *Screenshot: General Ledger Entries showing previously-applied entries back to Open status.*

---

## Partial applications

You can apply entries that don't fully net to zero. For example, applying a +500 debit against a −300 credit:

| Entry | Before | After |
|---|---|---|
| +500 (debit) | Open = Yes, Remaining = 500 | Open = Yes, Remaining = 200 |
| −300 (credit) | Open = Yes, Remaining = −300 | Open = No, Remaining = 0 |

The credit entry is fully settled. The debit entry stays open with the remaining 200, ready for further applications.

> 📸 *Screenshot: Apply G/L Entries worksheet after a partial application, showing the base entry still open with a reduced Remaining Amount.*

---

## Viewing the application history

Every application creates a full audit trail in the **GL Entry Application Entries** page. Each record shows:

| Field | Description |
|---|---|
| **G/L Entry No.** | The entry this record belongs to |
| **Applied G/L Entry No.** | The counterparty entry |
| **Applied Amount** | The amount applied |
| **Application Date** | When the application was posted |
| **User ID** | Who performed the application |
| **Reversed** | Whether this application has been undone |

Applications always create **two** records (bidirectional): one from each entry's perspective. This ensures you can look up the application history from either side.

> 📸 *Screenshot: GL Entry App. Entries page showing bidirectional application records.*

---

## NL migration (legacy data)

If your database previously used the **Dutch (NL) localization** for applying G/L entries, the app automatically migrates your historical application data during installation. No manual steps are required.

### What happens during migration

1. The app detects NL-specific fields on the G/L Entry table (field 11301)
2. Existing application data (Open status, Remaining Amounts, Closed-by references) is migrated to the new data model
3. Bidirectional application records are created in the new GL Entry Application table
4. Results are logged to the **Migration Log**

### Viewing migration results

A notification appears on the **General Ledger Entries** page after migration completes. Click the notification or open the **Migration Log** from the action bar to review:

- Number of entries migrated
- Number of applications created
- Any data quality issues detected and repaired

> 📸 *Screenshot: Migration notification on the General Ledger Entries page.*

> 📸 *Screenshot: Apply GL Migration Log page showing migration results.*

---

## Keyboard shortcuts

| Shortcut | Action | Where |
|---|---|---|
| **Shift+F11** | Open Apply G/L Entries worksheet | General Ledger Entries page |
| **F7** | Set / clear Applies-to ID | Apply G/L Entries worksheet |
| **F9** | Post Application | Apply G/L Entries worksheet |
| **Alt+D** | View Dimensions | Apply G/L Entries worksheet |

---

## Troubleshooting

| Issue | Cause | Solution |
|---|---|---|
| "Cannot set Applies-to ID on entry X because it is not open" | Entry is already fully applied | Undo the existing application first, or choose a different entry |
| "All entries must belong to the same G/L Account" | Selected entries span multiple accounts | Only apply entries within the same G/L account |
| "A G/L Entry cannot be applied to itself" | Same entry selected as both base and target | Select a different matching entry |
| "There are no entries selected for application" | Applies-to ID was not set on any matching entry | Press F7 on at least two entries before posting |
| Applied Amount doesn't match expectations | Partial application or prior applications exist | Check Applied Entries to review the full application history |

---

## Permissions

The app includes the following permission sets:

| Permission Set | Description |
|---|---|
| **Apply GL - Basic** | Read/write access to application tables — assign to users who apply entries |
| **Apply GL - Premium** | Extended permissions for advanced operations |

Assign the appropriate permission set via **User Setup** or **Permission Sets** in Business Central.

---

## Support

For questions or issues, contact **bydynamics** support or visit our support site.


______________________________________________________________________

[back](../README.md)
