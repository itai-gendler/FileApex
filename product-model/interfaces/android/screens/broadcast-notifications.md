---
entities:
- entity: device-settings
  shows:
  - Share notifications
  - Share notifications with
  - Verification codes
  - Shared apps
  - Sync dismissal
  collects:
  - Share notifications
  - Share notifications with
  - Verification codes
  - Shared apps
  - Sync dismissal
- entity: paired-device
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsBroadcastNotificationsPage.kt
---

# Broadcast Notifications

Settings → Notifications → Broadcast Notifications on a phone: whether it shares its notifications, with which paired device, from which apps, whether verification codes go too, and whether reading on the other device clears them here.
