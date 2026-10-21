---
entities:
- entity: device-file
  shows:
  - Name
  - Kind
  - Size
  - Date modified
  - Folder
- entity: paired-device
  shows:
  - Name
  - Online
- entity: pending-copy
  shows:
  - Files
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/FileExplorerScreen.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/explorer/ExplorerBody.kt
---

# Local Files

This device's own folders, with the same actions as a browsed device plus the pending copy ready to paste here.
