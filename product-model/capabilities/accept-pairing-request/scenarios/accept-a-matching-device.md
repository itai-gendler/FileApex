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
- text: "The User sees the same check code on both screens and chooses Codes match, pair"
  kind: actor
  actor: user
  entities:
  - { entity: pairing-request, effect: reads, facts: [Device name, Check code] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The Product pairs the two devices, each keeping the other's name, address and security key"
  kind: product
  actor: user
  entities:
  - { entity: pairing-request, effect: changes, from: Waiting, to: Accepted, facts: [] }
  - { entity: paired-device, as: joiner, effect: creates, to: Paired, facts: [Name, Platform, Make and model, App version, Online, Last seen, Address, Requires PIN, Security key, Position] }
  - { entity: paired-device, as: host, effect: creates, to: Paired, facts: [Name, Platform, Make and model, App version, Online, Last seen, Address, Requires PIN, Security key, Position] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The Product stops the broadcast; the code takes no other request"
  kind: product
  actor: user
  entities:
  - { entity: pairing-code, effect: changes, from: Broadcasting, to: Used, facts: [Time left] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The Product says it is paired with the new device and sends it the whole Bulletin Board"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, as: joiner, effect: reads, facts: [Name] }
  - { entity: bulletin-message, effect: reads, facts: [Text, Kind, Sender, Posted at, Locked] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
---

# Accept a matching device

## Trigger

A device the User is joining asks to pair.

## Outcome

The two devices are Paired on both sides; the joining device receives the board without a notification for each old message.
