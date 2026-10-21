---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Switch Device on Home and picks a device"
  kind: actor
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android::home
    desktop:
      place: desktop::home
- text: "The Product shows that device on Home and remembers it"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: changes, facts: [Connected device] }
  contexts:
    android:
      place: android::home
    desktop:
      place: desktop::home
- text: "On a computer, the Product tells the phone it showed before to stop sending notifications, and the new phone to start"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name, Platform] }
  contexts:
    android:
      place: android::home
    desktop:
      place: desktop::home
---

# Show another device

## Trigger

The User has more than one device and wants another on Home.

## Outcome

Home shows the chosen device, and a computer takes notifications from that phone only.
