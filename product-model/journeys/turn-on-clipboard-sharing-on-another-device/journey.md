---
actors:
- user
references:
- kind: code
  role: implementation
  target: composeApp/src/commonMain/kotlin/com/fileapex/App.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerClipboardRoutes.kt
---

# Turn on clipboard sharing on another device

## Goal

The User gets clipboard sharing working on a device where it is off, without hunting for the setting there.

## Success criterion

Clipboard Sharing is on on the other device, and clipboard text reaches it.
