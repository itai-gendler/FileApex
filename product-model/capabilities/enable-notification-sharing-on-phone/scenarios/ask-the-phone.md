---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: "Home shows a connected phone that is not sharing its notifications"
  kind: condition
  entities:
  - { entity: device-settings, effect: reads, facts: [Connected device] }
  - { entity: paired-device, effect: reads, facts: [Name, Online] }
  contexts:
    desktop:
      place: desktop::home
- text: "The User chooses Enable on phone"
  kind: actor
  actor: user
  entities: []
  contexts:
    desktop:
      place: desktop::home
- text: "The Product asks the phone to show a prompt that opens its Broadcast Notifications"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Address] }
  contexts:
    desktop:
      place: desktop::home
- text: "The Product says to check the phone and tap the notification, and waits for the phone to finish setup, checking every few seconds"
  kind: product
  actor: user
  entities: []
  contexts:
    desktop:
      place: desktop::home
---

# Ask the phone to share

## Trigger

The User wants the phone's notifications on the computer.

## Outcome

The phone shows "Enable notification access"; once it shares, the counts appear on Home.
