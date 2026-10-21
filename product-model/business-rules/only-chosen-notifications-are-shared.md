---
appliesTo:
- type: capability
  id: change-broadcast-notifications-settings
- type: capability
  id: read-phone-notifications
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/notifications/NotificationBroadcastPolicy.kt#NotificationBroadcastPolicy
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/notifications/NotificationBroadcaster.kt#NotificationBroadcaster
---

# Only notifications from the apps turned on are shared

A phone shares a notification only from an app the User turned on, and never one that is ongoing, silent, a group summary or FileApex's own. A notification that looks like a sign-in or verification code stays on the phone unless Verification codes is on. Everything is encrypted for the one device chosen under Share with.
