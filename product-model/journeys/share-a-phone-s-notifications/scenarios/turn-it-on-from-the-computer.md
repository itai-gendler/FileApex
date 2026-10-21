---
kind: primary
result: achieved
routes:
  from-the-computer: From the computer
steps:
- text: "The User chooses Enable on phone on the computer's Home"
  kind: actor
  actor: user
  capability: enable-notification-sharing-on-phone
  entities: []
  contexts:
    from-the-computer:
      place: desktop::home
- text: "The Product asks the phone to show its prompt, and the phone shows \"Enable notification access\""
  kind: product
  actor: user
  capability: enable-notification-sharing-on-phone
  entities: []
  contexts:
    from-the-computer:
      place: desktop::home
- text: "The User taps the notification on the phone, which opens Broadcast Notifications"
  kind: actor
  actor: user
  capability: change-broadcast-notifications-settings
  entities: []
  contexts:
    from-the-computer:
      place: android::broadcast-notifications
- text: "The User turns on Share notifications, agrees to the disclosure, grants notification access and turns on the apps to share"
  kind: actor
  actor: user
  capability: change-broadcast-notifications-settings
  entities:
  - { entity: device-settings, effect: reads, facts: [Share notifications, Shared apps] }
  contexts:
    from-the-computer:
      place: android::broadcast-notifications
- text: "The Product saves the choices on the phone"
  kind: product
  actor: user
  capability: change-broadcast-notifications-settings
  entities:
  - { entity: device-settings, effect: changes, facts: [Share notifications, Share notifications with, Shared apps] }
  contexts:
    from-the-computer:
      place: android::broadcast-notifications
- text: "The computer sees the phone is now sharing and shows its notification counts on Home"
  kind: product
  actor: user
  capability: read-phone-notifications
  entities:
  - { entity: phone-notification, effect: reads, facts: [Category] }
  contexts:
    from-the-computer:
      place: desktop::home
---

# Turn it on from the computer

## Trigger

The computer's Home shows a phone that is not sharing yet.

## Outcome

The phone shares its chosen apps' notifications with the computer.
