---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: "Home shows a phone that shares its notifications"
  kind: condition
  entities:
  - { entity: device-settings, effect: reads, facts: [Connected device] }
  - { entity: paired-device, effect: reads, facts: [Name] }
  contexts:
    desktop:
      place: desktop::home
- text: "The Product counts the phone's notifications as Messages, Emails and Other Notifications"
  kind: product
  actor: user
  entities:
  - { entity: phone-notification, effect: reads, facts: [Category] }
  contexts:
    desktop:
      place: desktop::home
- text: "The User opens Messages and picks a conversation"
  kind: actor
  actor: user
  entities:
  - { entity: phone-notification, effect: reads, facts: [Category, From, Text] }
  contexts:
    desktop:
      place: desktop::home
- text: "The Product shows the conversation's recent lines, messages grouped by sender or chat, other notifications by app, each email on its own"
  kind: product
  actor: user
  entities:
  - { entity: phone-notification, effect: reads, facts: [App, From, Title, Text, Posted at] }
  contexts:
    desktop:
      place: desktop::home
- text: "The User goes back or closes the list"
  kind: actor
  actor: user
  entities: []
  contexts:
    desktop:
      place: desktop::home
- text: "The Product clears what was read here and asks the phone to dismiss it, which it does when Sync dismissal is on"
  kind: product
  actor: user
  entities:
  - { entity: phone-notification, effect: removes }
  - { entity: device-settings, effect: reads, facts: [Sync dismissal] }
  contexts:
    desktop:
      place: desktop::home
---

# Read a conversation

## Trigger

The phone is in another room and messages keep arriving.

## Outcome

The User has read the messages on the computer, and they are cleared here and, with Sync dismissal, on the phone.
