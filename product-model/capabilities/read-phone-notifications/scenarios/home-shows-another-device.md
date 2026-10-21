---
kind: edge
routes:
  desktop: Desktop app
steps:
- text: "Home is closed, or shows a different device, or the computer stops asking for more than ten minutes"
  kind: condition
  unattended: true
  entities:
  - { entity: device-settings, effect: reads, facts: [Connected device] }
  contexts:
    desktop:
      place: desktop::home
- text: "The phone stops sending notifications to this computer, and the computer takes none from it"
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop::home
---

# Home shows another device

## Trigger

The User switched device, theme or window.

## Outcome

No notifications from that phone arrive until Home shows it again, when the phone's current list is fetched afresh.
