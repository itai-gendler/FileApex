---
appliesTo:
- type: entity
  id: phone-notification
  effect: creates
- type: capability
  id: read-phone-notifications
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/notifications/NotificationInbox.kt#NotificationInbox
- kind: doc
  role: intent
  target: PRIVACY.md
---

# Phone notifications are never stored on the receiving device

A computer keeps the phone's notifications in memory only, at most 200 of them, and loses them when it closes. After waking or reconnecting, it fetches the phone's current list again; the phone's own notification shade is the record.
