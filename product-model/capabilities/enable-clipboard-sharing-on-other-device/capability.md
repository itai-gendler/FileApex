---
availability:
- { place: android }
- { place: desktop }
domain: home
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/adaptive/simple/SimpleOverview.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/notifications/NotificationBroadcaster.kt#NotificationBroadcaster
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerNotificationRoutes.kt
---

# Enable clipboard sharing on the other device

From Home in the Simple layout, ask the connected device to open its clipboard settings when its clipboard sharing is off.
