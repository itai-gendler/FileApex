---
availability:
- { place: android }
domain: notifications
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsBroadcastNotificationsPage.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/notifications/NotificationBroadcastPolicy.kt#NotificationBroadcastPolicy
- kind: code
  role: implementation
  target: shared/src/androidMain/kotlin/com/fileapex/platform/FileApexNotificationListenerService.kt
---

# Change Broadcast Notifications settings

On an Android phone, choose in Settings → Notifications → Broadcast Notifications whether it shares its notifications, with which one paired device, from which apps, whether verification codes go too, and whether reading on the other device clears them here.
