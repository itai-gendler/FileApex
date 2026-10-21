---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User opens Settings → Notifications and switches Bulletin Board and File Transfer on or off"
  kind: actor
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Bulletin Board notifications, File Transfer notifications] }
  contexts:
    android:
      place: android::notification-settings
    desktop:
      place: desktop::notification-settings
- text: "The Product saves the switches"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: changes, facts: [Bulletin Board notifications, File Transfer notifications] }
  contexts:
    android:
      place: android::notification-settings
    desktop:
      place: desktop::notification-settings
---

# Choose which events notify

## Trigger

The User wants fewer, or more, alerts.

## Outcome

New messages and received files notify as set.
