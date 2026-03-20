# Viewing the application history

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

[← Previous: Partial applications](PartialApplications.md) | [Next: NL migration (legacy data) →](NLMigration.md)
