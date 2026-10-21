---
appliesTo:
- type: capability
  id: read-phone-notifications
- type: capability
  id: switch-device
- type: capability
  id: enable-notification-sharing-on-phone
- type: entity
  id: phone-notification
  effect: creates
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/notifications/NotificationCompanion.kt#NotificationCompanion
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/notifications/NotificationCompanionGrant.kt#NotificationCompanionGrant
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/adaptive/SimpleHome.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerNotificationRoutes.kt
---

# A computer takes notifications only from the phone its Home shows

A computer asks for notifications from one phone: the one Home shows in the Simple layout, while Home is on screen. The phone sends only while that request is live, and stops ten minutes after the computer last renewed it; the computer refuses notifications from any other phone. Other layouts do not show phone notifications.
