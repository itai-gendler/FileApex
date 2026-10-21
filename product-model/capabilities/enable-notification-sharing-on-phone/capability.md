---
availability:
- { place: desktop }
domain: home
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/adaptive/simple/SimpleNotifications.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/notifications/NotificationBroadcaster.kt#NotificationBroadcaster
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerNotificationRoutes.kt
---

# Enable notification sharing on the phone

From Home on a computer, ask the connected phone to start sharing its notifications with Enable on phone. Nothing is shared until the User turns it on on the phone itself.
