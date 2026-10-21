---
domain: bulletin-board
references:
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/data/bulletin/BulletinBoardEntities.kt#MessageEntity}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/data/note/NoteRecord.kt#NoteRecord}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/data/bulletin/BulletinBoardPolicy.kt}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/data/bulletin/BulletinDeleteContentKind.kt}
---

# Bulletin message

One post on the Bulletin Board: text, a link, a file or image, or a low battery alert. Every paired device keeps its own copy of the board.

## Information kept

- **Text** — the message, or the caption of a file.
- **Kind** — message, web link, file, image, or battery alert.
- **Sender** — the device that posted it, under the name that device now has.
- **Posted at** — when it was posted; the board groups messages by day.
- **Attachment name** — the attached file's name.
- **Attachment size** — the attached file's size.
- **Preview** — a small preview of an attached image, carried with the message.
- **Locked** — whether it is locked; a locked message is never deleted.
- **Downloaded** — whether the attached file is already on this device.

## States

### Posted

On the board.

### Deleted

Taken off the board on this device, or on every device, and its notification withdrawn. It does not come back.
