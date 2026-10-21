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
  target: shared/src/commonMain/kotlin/com/fileapex/domain/transfer/TransferActivityGuard.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/LiveTransferBanner.kt
---

# Cancel a transfer

Stop a send while it is going out, from the transfer in progress or from Queued Files. A cancelled send stays in Queued Files, paused, until it is retried or removed.
