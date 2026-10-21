---
availability:
- { place: android }
- { place: desktop }
domain: bulletin-board
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/notes/NoteBubbleItem.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/bulletin/BulletinBoardDaos.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/NotesViewModel.kt
---

# Lock a message

Lock a message on the Bulletin Board with Lock attachment, so it is never deleted and shows under Pinned.
