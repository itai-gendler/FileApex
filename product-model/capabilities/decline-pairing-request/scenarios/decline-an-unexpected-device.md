---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "A request arrives while the code is broadcast"
  kind: condition
  entities:
  - { entity: pairing-code, effect: reads, facts: [Code] }
  - { entity: pairing-request, effect: reads, facts: [Device name] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The Product shows the joining device's name and the check code, and asks whether to pair"
  kind: product
  actor: user
  entities:
  - { entity: pairing-request, effect: reads, facts: [Device name, Check code, Hint] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The User sees a different check code, or a device they did not expect, and chooses Decline"
  kind: actor
  actor: user
  entities:
  - { entity: pairing-request, effect: reads, facts: [Device name, Check code, Hint] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The Product turns the request down and ends the code"
  kind: product
  actor: user
  entities:
  - { entity: pairing-request, effect: changes, from: Waiting, to: Declined, facts: [] }
  - { entity: pairing-code, effect: changes, from: Broadcasting, to: Used, facts: [Time left] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The Product tells the joining device it was declined; nothing about it is kept"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
---

# Decline an unexpected device

## Trigger

Someone asks to pair whom the User did not invite, or the codes do not match.

## Outcome

Nothing is paired and the code no longer works; Retry makes a new one.
