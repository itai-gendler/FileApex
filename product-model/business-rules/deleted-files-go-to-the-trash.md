---
appliesTo:
- type: capability
  id: delete-file-on-device
- type: entity
  id: device-file
  effect: removes
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerWriteGate.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/explorer/ExplorerMutationActions.kt
---

# A file deleted from another device goes to that device's Trash

Deleting in another device's folders never raises a question on that device and never deletes for good: a phone keeps the files in FileApex's Trash, restorable from Tools, and a computer moves them to the system trash. Only files under the device's browsable root can be deleted this way.
