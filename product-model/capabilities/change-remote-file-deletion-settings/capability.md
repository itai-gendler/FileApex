---
availability:
- { place: android }
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsRemoteFileDeletionPage.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/bulletin/BulletinRemoteFilePurgeHandler.kt#BulletinRemoteFilePurgeHandler
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/bulletin/BulletinRemoteFilePurgePolicy.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/notes/NotesDialogs.kt
---

# Change remote file deletion settings

On a phone, decide in Settings → Bulletin Board → Delete on Remote Devices whether a delete sent from another device may also delete the file downloaded here, or answer the same question the first time such a delete arrives.
