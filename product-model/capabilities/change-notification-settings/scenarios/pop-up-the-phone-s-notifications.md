---
kind: alternate
routes:
  desktop: Desktop app
steps:
- text: "The User turns on Notifications from connected phone on a Windows computer"
  kind: actor
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Notifications from connected phone] }
  contexts:
    desktop:
      place: desktop::notification-settings
- text: "The Product shows each notification the connected phone shares as a Windows notification too"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: changes, facts: [Notifications from connected phone] }
  contexts:
    desktop:
      place: desktop::notification-settings
---

# Pop up the phone's notifications on Windows

## Trigger

The User wants to see the phone's notifications without opening FileApex.

## Outcome

Shared notifications pop up on the computer; Windows may keep them in its own history.
