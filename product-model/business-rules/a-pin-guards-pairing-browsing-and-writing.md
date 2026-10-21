---
appliesTo:
- type: capability
  id: join-device
- type: capability
  id: browse-device-files
- type: capability
  id: preview-file
- type: capability
  id: download-device-files
- type: capability
  id: paste-device-files
- type: capability
  id: delete-file-on-device
- type: capability
  id: send-clipboard
- type: capability
  id: change-pin-settings
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/FileApexServer.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerWriteGate.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerFileRoutes.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerClipboardRoutes.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsPinRequiredPage.kt
---

# With Require PIN on, other devices need the PIN for everything but sending files

Pairing with the device, listing and opening its files, writing anywhere but its receive folder, deleting its files, and sending it clipboard text or notifications all need its PIN. Files sent to its receive folder never do. The PIN is kept only on the device that set it.
