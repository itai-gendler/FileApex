---
availability:
- { place: android }
- { place: desktop }
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/explorer/ExplorerMutationActions.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerWriteGate.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/explorer/ItemContextMenu.kt
---

# Delete a file on another device

Delete files in another device's folders after confirming. They go to that device's Trash.
