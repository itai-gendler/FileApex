---
appliesTo:
- type: capability
  id: send-clipboard
- type: entity
  id: clipboard-item
  effect: changes
  to: Delivered
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/clipboard/ClipboardShareCoordinator.kt#ClipboardShareCoordinator
---

# A shared link opens in the receiving device's browser

When clipboard text that arrives is a web address, the receiving device opens it in its default browser as well as putting it on the clipboard.
