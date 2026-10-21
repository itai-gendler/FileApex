---
appliesTo:
- type: capability
  id: post-bulletin-message
- type: capability
  id: view-bulletin-board
- type: entity
  id: bulletin-message
  effect: creates
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/bulletin/BulletinBoardSyncEngine.kt#BulletinBoardSyncEngine
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/bulletin/BulletinBoardPolicy.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/note/NoteRepository.kt#NoteRepository
---

# A post reaches every paired device's board

A message posted on one device goes to every paired device except Docker nodes, which have no board. A device that is away gets what it missed when it is back, and a newly paired device receives the whole board without a notification for each old message. A post that cannot be delivered for seven days is dropped for that device.
