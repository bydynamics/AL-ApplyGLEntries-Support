# Troubleshooting

| Issue | Cause | Solution |
|---|---|---|
| "Cannot set Applies-to ID on entry X because it is not open" | Entry is already fully applied | Undo the existing application first, or choose a different entry |
| "All entries must belong to the same G/L Account" | Selected entries span multiple accounts | Only apply entries within the same G/L account |
| "A G/L Entry cannot be applied to itself" | Same entry selected as both base and target | Select a different matching entry |
| "There are no entries selected for application" | Applies-to ID was not set on any matching entry | Press F7 on at least two entries before posting |
| Applied Amount doesn't match expectations | Partial application or prior applications exist | Check Applied Entries to review the full application history |

---

[← Previous: Keyboard shortcuts](KeyboardShortcuts.md) | [Next: Permissions →](Permissions.md)
