---
kind: alternate
routes:
  desktop: Desktop app
steps:
- text: "The phone posts a notification from an app it shares, while the computer shows that phone on Home"
  kind: condition
  unattended: true
  entities:
  - { entity: device-settings, effect: reads, facts: [Shared apps, Connected device] }
  contexts:
    desktop:
      place: desktop::home
- text: "The phone sends it encrypted to the computer, which adds it to the counts in memory only"
  kind: product
  entities:
  - { entity: phone-notification, effect: creates, facts: [App, Category, From, Title, Text, Can reply, Posted at] }
  contexts:
    desktop:
      place: desktop::home
---

# A notification arrives

## Trigger

Something happens on the phone.

## Outcome

The new notification is counted on Home within moments.

## Edge cases

- Ongoing and silent notifications, and FileApex's own, are never sent; ones with a verification code are sent only when Verification codes is on.
