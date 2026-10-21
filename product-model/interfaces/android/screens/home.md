---
entities:
- entity: paired-device
  shows:
  - Name
  - Make and model
  - Online
- entity: device-settings
  shows:
  - Connected device
  collects:
  - Connected device
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/adaptive/SimpleHome.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/adaptive/simple/SimpleOverview.kt
---

# Home

Home in the Simple layout: the one connected device, its make, battery and storage, whether clipboard sharing is on.
