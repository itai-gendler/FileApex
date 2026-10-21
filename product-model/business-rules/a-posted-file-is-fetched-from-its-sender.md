---
appliesTo:
- type: capability
  id: post-bulletin-message
- type: capability
  id: open-attachment
- type: entity
  id: bulletin-message
  effect: changes
  facts: [Downloaded]
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/bulletin/BulletinBoardSyncEngine.kt#BulletinBoardSyncEngine
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/cloud/drive/DriveRelayPolicy.kt#DriveRelayPolicy
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerBulletinRoutes.kt
---

# A posted file stays with its sender until it is opened

Posting a file sends its name, size and, for an image, a small preview. The file itself is fetched from the device that posted it the first time someone opens it on another device, and checked against what was posted. Over the local network a posted file is at most 35 MB; Google Drive Relay carries larger ones up to its own limit.
