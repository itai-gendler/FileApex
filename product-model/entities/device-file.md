---
references:
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/data/files/LocalFileRepository.kt}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerFileRoutes.kt}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/platform/UniqueFileNames.kt}
---

# Device file

A file or folder on one of the devices: on this one under Local Files, or on another one while it is browsed.

## Information kept

- **Name** — the file or folder name.
- **Kind** — a file or a folder.
- **Size** — the file's size.
- **Date modified** — when it last changed.
- **Folder** — where it sits on its device, below that device's browsable root.
