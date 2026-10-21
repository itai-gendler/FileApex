---
appliesTo:
- type: entity
  id: queued-file
  effect: changes
  to: Paused
- type: capability
  id: retry-queued-file
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/transfer/TransferQueueCoordinator.kt#TransferQueueCoordinator
---

# A file changed after it was queued is held back

A waiting send checks that each file still has the size and date it had when it was queued. A file changed since is not sent: the send is paused, saying the file changed after it was queued.
