---
entities:
- entity: device-settings
  shows:
  - Clipboard Sharing
  - Share clipboard with
  - Clipboard devices
  - Send Clipboard button
  - Accessibility
  - Via Cellular
  collects:
  - Clipboard Sharing
  - Share clipboard with
  - Clipboard devices
  - Send Clipboard button
  - Accessibility
  - Via Cellular
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
