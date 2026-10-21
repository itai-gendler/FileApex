---
appliesTo:
- type: capability
  id: send-clipboard
- type: capability
  id: change-clipboard-settings
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/clipboard/ClipboardShareCoordinator.kt#ClipboardShareCoordinator
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/clipboard/ClipboardSharePolicy.kt#ClipboardSharePolicy
---

# From a phone, Send Clipboard and copies reach only computers

When a phone sends its clipboard to the devices chosen under Share clipboard with, whether with Send Clipboard, the tile or a noticed copy, only the computers among them get it. Sending to one phone takes Send clipboard on that device. A computer sends to every chosen device.
