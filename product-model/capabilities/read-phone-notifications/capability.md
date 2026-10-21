---
availability:
- { place: desktop }
domain: home
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/adaptive/SimpleHome.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/adaptive/simple/SimpleNotifications.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/adaptive/SimpleNotificationList.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/notifications/NotificationCompanion.kt#NotificationCompanion
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/notifications/NotificationCompanionGrant.kt#NotificationCompanionGrant
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/notifications/NotificationThreads.kt#NotificationThreads
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerNotificationRoutes.kt
---

# Read phone notifications

On a computer, read the connected phone's notifications from Home, sorted into Messages, Emails and Other Notifications. They reach the computer only while Home shows that phone, and reading them clears them on both devices.
