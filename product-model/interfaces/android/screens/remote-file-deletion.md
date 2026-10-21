---
entities:
- entity: device-settings
  shows:
  - Allow remote file deletion
  collects:
  - Allow remote file deletion
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsRemoteFileDeletionPage.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsBackupPage.kt
---

# Delete on Remote Devices

Settings → Bulletin Board → Delete on Remote Devices: whether a Bulletin Board delete sent from another device also deletes the downloaded file on this phone.
