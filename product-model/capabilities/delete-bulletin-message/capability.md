---
availability:
- { place: android }
- { place: desktop }
domain: bulletin-board
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/notes/NotesDialogs.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/NotesViewModel.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/note/NoteRepository.kt#NoteRepository
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/bulletin/BulletinRemoteFilePurgeHandler.kt#BulletinRemoteFilePurgeHandler
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/bulletin/BulletinBoardDaos.kt
---

# Delete a message

Delete a Bulletin Board message from this device only or from all paired devices, and for a file, choose whether phones also delete their downloaded copy. A locked message is never deleted.
