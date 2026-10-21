---
appliesTo:
- type: capability
  id: send-clipboard
- type: capability
  id: change-clipboard-settings
- type: entity
  id: device-settings
  effect: changes
  facts: [Clipboard Sharing]
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerClipboardRoutes.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/clipboard/ClipboardShareCoordinator.kt#ClipboardShareCoordinator
- kind: code
  role: implementation
  target: composeApp/src/commonMain/kotlin/com/fileapex/App.kt
---

# Clipboard text moves only between devices with Clipboard Sharing on

A device with Clipboard Sharing off neither sends nor takes clipboard text. A device that tries to send to it sends a Clipboard Sharing Request instead, which the other device shows once.
