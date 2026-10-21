---
availability:
- { place: desktop }
domain: home
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/adaptive/SimpleNotificationList.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/notifications/NotificationBroadcaster.kt#NotificationBroadcaster
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerNotificationRoutes.kt
---

# Reply to a phone message

Answer a message notification from the computer: the phone fills in the app's reply box as if the User had typed it there.
