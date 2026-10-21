---
kind: primary
routes:
  android: Android app
steps:
- text: "The User opens Broadcast Notifications and turns on Share notifications"
  kind: actor
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Share notifications] }
  contexts:
    android:
      place: android::broadcast-notifications
- text: "The Product explains that message and email text from the chosen apps will be sent end-to-end encrypted to the chosen device, and is never stored or sent to a server"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::broadcast-notifications
- text: "The User chooses Agree and continue and grants notification access in Android"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::broadcast-notifications
- text: "The User picks the device under Share with and turns on the apps to share"
  kind: actor
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Share notifications with, Shared apps] }
  - { entity: paired-device, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android::broadcast-notifications
- text: "The Product saves the choices and starts sharing new notifications from those apps"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: changes, facts: [Share notifications, Share notifications with, Shared apps] }
  contexts:
    android:
      place: android::broadcast-notifications
---

# Start sharing notifications

## Trigger

The User wants to read the phone's messages on a computer.

## Outcome

The phone shares notifications from the chosen apps with the one chosen device.

## Edge cases

- With a single paired device, it is the one notifications go to.
- Apps are grouped as Messaging, Email, Shopping, AI assistants, Health and fitness, Weather, Utilities and system, and Other apps; every app starts off.
