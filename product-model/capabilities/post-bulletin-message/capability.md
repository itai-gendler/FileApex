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
  target: shared/src/commonMain/kotlin/com/fileapex/data/bulletin/BulletinBoardRepository.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/notes/NotesLogic.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/cloud/drive/DriveRelayPolicy.kt#DriveRelayPolicy
---

# Post to the Bulletin Board

Post text, a link or a file to the Bulletin Board of every paired device: from the composer (Send note, Attach file, or a file dropped on the board), or from another app with Post to Bulletin Board.
