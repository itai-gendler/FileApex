---
appliesTo:
- type: capability
  id: delete-bulletin-message
- type: capability
  id: change-remote-file-deletion-settings
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/bulletin/BulletinRemoteFilePurgeHandler.kt#BulletinRemoteFilePurgeHandler
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/bulletin/BulletinRemoteFilePurgePolicy.kt
---

# Only the phone decides whether a remote delete removes its file

A delete for all devices with Remove File deletes the downloaded copy only on phones whose Allow remote file deletion is on; a phone that has not decided asks once and saves the answer. It never deletes the sender's own file, and touches only files in FileApex's downloads.
