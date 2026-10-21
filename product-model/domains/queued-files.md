---
references:
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/ui/TransferQueueScreen.kt}
---

# Queued Files

The list of sends still on their way, and stopping, retrying or removing them.

## Boundary

This domain does not own choosing files and devices to send to; that starts in Send To, a drop or the Share sheet.
