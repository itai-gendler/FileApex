---
availability:
- { place: android }
- { place: desktop }
domain: queued-files
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/TransferQueueScreen.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/TransferQueueViewModel.kt
---

# View queued files

Open Queued Files from the clock icon in the header to see every send still on its way, the devices it waits for, and why the last try did not finish.
