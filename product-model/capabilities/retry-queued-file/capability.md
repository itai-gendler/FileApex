---
availability:
- { place: android }
- { place: desktop }
domain: queued-files
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/transfer/TransferQueueCoordinator.kt#TransferQueueCoordinator
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/TransferQueueScreen.kt
---

# Retry a queued send

Send a paused or waiting send again at once with Retry now, without waiting for the next automatic try.
