---
references:
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/domain/clipboard/ClipboardShareCoordinator.kt#ClipboardShareCoordinator}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/domain/clipboard/ClipboardSharePolicy.kt#ClipboardSharePolicy}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/domain/clipboard/ClipboardSharingModels.kt}
---

# Clipboard item

Clipboard text on its way to other devices, encrypted separately for each one.

## Information kept

- **Text** — the copied text or link.
- **Copied at** — when it was taken from the clipboard.
- **Waiting for** — the devices it has not reached yet.

## States

### Sending

Being delivered, and tried again every few seconds for a device that has not taken it.

### Delivered

Every device it was meant for has it on its clipboard.

### Expired

Fifteen seconds passed since it was copied; it is no longer delivered to anyone.
