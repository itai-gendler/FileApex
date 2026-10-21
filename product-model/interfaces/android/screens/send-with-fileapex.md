---
entities:
- entity: device-file
  shows:
  - Name
- entity: paired-device
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/ShareSendScreen.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/ShareSendViewModel.kt
---

# Send with FileApex

The picker the Android Share sheet opens: the shared files and the paired devices to tick and send to.
