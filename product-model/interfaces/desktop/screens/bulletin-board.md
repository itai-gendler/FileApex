---
entities:
- entity: bulletin-message
  shows:
  - Text
  - Kind
  - Sender
  - Posted at
  - Attachment name
  - Attachment size
  - Preview
  - Locked
  - Downloaded
  collects:
  - Text
  - Attachment name
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/notes/NotesBody.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/notes/NotesListSection.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/notes/NotesComposer.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/notes/NoteBubbleItem.kt
---

# Bulletin Board

The shared board, grouped by day, newest at the bottom, with filters for links, images, documents, snippets, files, pinned messages and hashtags, and the composer that posts text or a file to every paired device.
