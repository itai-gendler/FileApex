---
kind: edge
routes:
  android: Android app
steps:
- text: "The User opens Broadcast Notifications after Android notification access was taken away"
  kind: actor
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Share notifications] }
  contexts:
    android:
      place: android::broadcast-notifications
- text: "The Product says notification access is off and offers to open the Android setting, and App info for Allow restricted settings when the switch is greyed out"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::broadcast-notifications
---

# Notification access is off

## Trigger

Android withdrew the permission, or it was never granted.

## Outcome

Nothing is shared until access is granted again.
