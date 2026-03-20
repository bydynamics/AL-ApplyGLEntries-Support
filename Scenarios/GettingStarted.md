# Getting started

## Installation

Install the app from **Microsoft AppSource** or via **Extension Management** in Business Central. No configuration is required — the app is ready to use immediately.

On first install, the app initializes all existing G/L entries as **Open** with **Remaining Amount** equal to their original **Amount**. This is a one-time process.

![New](https://github.com/bydynamics/AL-ApplyGLEntries-Support/blob/main/Assets/ScreenshotExtensionManagementpageshowingtheinstalledApplyGLEntriesextension.png)
> 📸 *Screenshot: Extension Management page showing the installed "Apply G/L Entries" extension.*

## New fields on General Ledger Entries

After installation, three new columns are available on the **General Ledger Entries** page (Page 20):

| Column | Description |
|---|---|
| **Open** | `Yes` if the entry is available for application; `No` if fully applied |
| **Remaining Amount** | The amount still available for application |
| **Applied Amount** | The total amount already applied |

![New](https://github.com/bydynamics/AL-ApplyGLEntries-Support/blob/main/Assets/ScreenshotGeneralLedgerEntriespageshowingtheOpenRemainingAmountandAppliedAmountcolumns.png)
> 📸 *Screenshot: General Ledger Entries page showing the Open, Remaining Amount, and Applied Amount columns.*

## New actions on General Ledger Entries

| Action | Shortcut | Description |
|---|---|---|
| **Apply Entries** | Shift+F11 | Opens the application worksheet for the selected G/L account |
| **Applied Entries** | — | Shows the application history for the selected entry |
| **Migration Log** | — | Shows the NL data migration log (if applicable) |

![New](https://github.com/bydynamics/AL-ApplyGLEntries-Support/blob/main/Assets/ScreenshotGeneralLedgerEntriespagewiththeApplicationactiongroupvisibleintheactionbar.png)
> 📸 *Screenshot: General Ledger Entries page with the "Application" action group visible in the action bar.*

---

[← Previous: What does Apply G/L Entries do?](WhatDoesApplyGLEntriesDo.md) | [Next: How to apply G/L entries →](HowToApplyGLEntries.md)
