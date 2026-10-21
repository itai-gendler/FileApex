---
entities:
- entity: device-settings
  shows:
  - Bulletin Board notifications
  - File Transfer notifications
  - Notifications from connected phone
  collects:
  - Bulletin Board notifications
  - File Transfer notifications
  - Notifications from connected phone
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsNotificationsPage.kt
---

# Notifications

Settings → Notifications: which events raise a notification on this device, and on Windows whether the connected phone's notifications pop up.
