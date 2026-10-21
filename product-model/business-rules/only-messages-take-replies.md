---
appliesTo:
- type: capability
  id: reply-to-phone-message
- type: capability
  id: read-phone-notifications
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/adaptive/SimpleNotificationList.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/notifications/NotificationThreads.kt#NotificationThreads
---

# Only message notifications can be answered

Replies are offered for Messages, on the latest notification in the conversation that the phone can fill in. The reply text is passed to the app on the phone and not kept by FileApex.
