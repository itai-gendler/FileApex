---
entities:
- entity: device-settings
  shows:
  - Clipboard Sharing
  - Share clipboard with
  - Clipboard devices
  - Automatically send
  collects:
  - Clipboard Sharing
  - Share clipboard with
  - Clipboard devices
  - Automatically send
- entity: paired-device
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsClipboardPage.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsClipboardShareTargetsPage.kt
---

# Clipboard

Settings → Clipboard: whether clipboard sharing is on and which devices it goes to, and, by platform, how copies are noticed and sent.
