---
references:
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/data/clipboard/TransferClipboard.kt}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/presentation/explorer/ExplorerCopyActions.kt}
---

# Pending copy

Files chosen with Copy, gathered on this device until the User pastes them into a folder or clears them. Each Copy adds to it. It is FileApex's own list, separate from the system clipboard, and lasts while the app runs.

## Information kept

- **Files** — the files waiting to be pasted.
- **Source** — the device each file was copied from.
