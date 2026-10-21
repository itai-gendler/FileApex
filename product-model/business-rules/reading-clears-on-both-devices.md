---
appliesTo:
- type: capability
  id: read-phone-notifications
- type: capability
  id: change-broadcast-notifications-settings
- type: entity
  id: phone-notification
  effect: removes
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

# Reading a notification on the computer clears it on both devices

A notification the User opens on the computer is cleared there when the list closes or the User goes back, and the phone dismisses it too when its Sync dismissal is on. A notification cleared on the phone always leaves the computer.
