---
entities:
- entity: queued-file
  shows:
  - Files
  - Waiting for
  - Queued at
  - Last error
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/TransferQueueScreen.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/QueuedFilesButton.kt
---

# Queued Files

Every send still on its way: the files, the devices it is waiting for, and why the last try did not finish.
