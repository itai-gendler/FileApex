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
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/explorer/ItemContextMenu.kt
---

# Device browser

The folders of another device, from its browsable root down, with each item's size and date, the pending copy ready to paste, and the actions on what is selected.
