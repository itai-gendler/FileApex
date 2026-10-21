---
appliesTo:
- type: capability
  id: send-device-files
- type: capability
  id: paste-device-files
- type: capability
  id: download-device-files
- type: entity
  id: device-file
  effect: creates
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/platform/UniqueFileNames.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerFileRoutes.kt
---

# A received file never replaces one already there

When a file of the same name is already in place, the new one is saved as "name (1)" and so on. An interrupted file resumes from where it stopped, and a file whose content does not match what was sent is discarded.
