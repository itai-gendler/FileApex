---
references:
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsNotificationsPage.kt}
---

# Notifications

Settings → Notifications: which events raise a notification on this device, and, on a phone, Broadcast Notifications.

## Boundary

This domain does not own reading or answering a phone's notifications on a computer; that is on Home.
