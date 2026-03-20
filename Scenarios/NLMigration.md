# NL migration (legacy data)

If your database previously used the **Dutch (NL) localization** for applying G/L entries, the app automatically migrates your historical application data during installation. No manual steps are required.

## What happens during migration

1. The app detects NL-specific fields on the G/L Entry table (field 11301)
2. Existing application data (Open status, Remaining Amounts, Closed-by references) is migrated to the new data model
3. Bidirectional application records are created in the new GL Entry Application table
4. Results are logged to the **Migration Log**

## Viewing migration results

A notification appears on the **General Ledger Entries** page after migration completes. Click the notification or open the **Migration Log** from the action bar to review:

- Number of entries migrated
- Number of applications created
- Any data quality issues detected and repaired

> 📸 *Screenshot: Migration notification on the General Ledger Entries page.*

> 📸 *Screenshot: Apply GL Migration Log page showing migration results.*

---

[← Previous: Viewing the application history](ViewingTheApplicationHistory.md) | [Next: Keyboard shortcuts →](KeyboardShortcuts.md)
