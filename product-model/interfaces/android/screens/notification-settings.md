---
entities:
- entity: device-settings
  shows:
  - Bulletin Board notifications
  - File Transfer notifications
  - Live activity
  collects:
  - Bulletin Board notifications
  - File Transfer notifications
  - Live activity
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsNotificationsPage.kt
---

# Notifications

Settings → Notifications: which events raise a notification on this device, and the way into Broadcast Notifications.
