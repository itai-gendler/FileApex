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
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/TransferQueueViewModel.kt
---

# Remove a queued send

Take a send out of Queued Files with Remove from queue, so it is never delivered to the devices still waiting.
