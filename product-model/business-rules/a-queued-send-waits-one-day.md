---
appliesTo:
- type: entity
  id: queued-file
  effect: removes
- type: capability
  id: view-queued-files
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/transfer/TransferQueueCoordinator.kt#TransferQueueCoordinator
---

# A queued send waits at most a day

A send that has not reached every device 24 hours after it was made is taken out of Queued Files, paused or not.
