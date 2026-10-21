---
appliesTo:
- type: capability
  id: delete-bulletin-message
- type: capability
  id: lock-bulletin-message
- type: capability
  id: unlock-bulletin-message
- type: entity
  id: bulletin-message
  effect: changes
  to: Deleted
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/bulletin/BulletinBoardDaos.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/note/NoteRepository.kt#NoteRepository
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/NotesViewModel.kt
---

# A locked message is never deleted

A locked message cannot be deleted on its device until it is unlocked; a delete for all devices that arrives from another device leaves it in place; a request to delete its downloaded file is ignored; and the 90-day clean-up skips it.
