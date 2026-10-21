---
appliesTo:
- type: capability
  id: send-clipboard
- type: entity
  id: clipboard-item
  effect: creates
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/clipboard/ClipboardE2ee.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/clipboard/ClipboardSenderCheck.kt
---

# Clipboard text is encrypted for each receiving device

Clipboard text is encrypted on the sending device for each paired device separately, and a device takes it only from a paired device whose key it holds. Over cellular it travels the same way, sealed, through the cloud relay.
