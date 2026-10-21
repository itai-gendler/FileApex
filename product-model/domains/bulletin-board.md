---
references:
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/ui/notes/NotesBody.kt}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/presentation/NotesViewModel.kt}
---

# Bulletin Board

The board every paired device shares: posting text, links and files, opening attachments, locking and deleting messages, and the low battery alerts phones post.

## Boundary

This domain does not own sending files to a device's receive folder, or the clipboard; those go straight to the chosen devices and are not kept on a board.
