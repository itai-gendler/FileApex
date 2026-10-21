---
availability:
- { place: android }
- { place: desktop }
domain: bulletin-board
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/note/NoteRepository.kt#NoteRepository
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/bulletin/BulletinBoardSyncEngine.kt#BulletinBoardSyncEngine
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerBulletinRoutes.kt
---

# Open an attachment

Open a file posted on the Bulletin Board. A file posted on another device is fetched from that device the first time, checked against what was posted, and kept here.
