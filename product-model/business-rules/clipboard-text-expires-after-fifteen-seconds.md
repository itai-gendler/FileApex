---
appliesTo:
- type: capability
  id: send-clipboard
- type: entity
  id: clipboard-item
  effect: changes
  to: Expired
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/clipboard/ClipboardSharePolicy.kt#ClipboardSharePolicy
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/clipboard/ClipboardShareCoordinator.kt#ClipboardShareCoordinator
---

# Clipboard text is delivered only within 15 seconds of the copy

A clipboard send is retried every few seconds for devices that have not taken it, and stops 15 seconds after the text was copied. A receiving device refuses text older than that, so no device gets stale clipboard text later.
