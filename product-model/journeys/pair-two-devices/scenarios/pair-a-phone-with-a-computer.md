---
kind: primary
result: achieved
routes:
  phone-joins: Phone joins a computer
steps:
- text: "The User chooses Add New Device, then Generate QR Code on the computer"
  kind: actor
  actor: user
  capability: generate-pairing-code
  entities: []
  contexts:
    phone-joins:
      place: desktop::devices
- text: "The Product shows and broadcasts a fresh 6-digit code"
  kind: product
  actor: user
  capability: generate-pairing-code
  entities:
  - { entity: pairing-code, effect: creates, to: Broadcasting, facts: [Code, Device name, QR code, Time left] }
  contexts:
    phone-joins:
      place: desktop::generate-qr-code
- text: "The User chooses Join device on the phone and confirms the code it filled in from the broadcast"
  kind: actor
  actor: user
  capability: join-device
  entities:
  - { entity: pairing-code, effect: reads, facts: [Code, Device name] }
  contexts:
    phone-joins:
      place: android::join-device
- text: "The User compares the check code with the computer's screen and chooses Codes match"
  kind: actor
  actor: user
  capability: join-device
  entities: []
  contexts:
    phone-joins:
      place: android::join-device
- text: "The Product sends the request to the computer, which asks its User whether to pair"
  kind: product
  actor: user
  capability: join-device
  entities:
  - { entity: pairing-request, effect: creates, to: Waiting, facts: [Device name, Check code, Hint] }
  contexts:
    phone-joins:
      place: desktop::generate-qr-code
- text: "The User sees the same check code on the computer and chooses Codes match, pair"
  kind: actor
  actor: user
  capability: accept-pairing-request
  entities:
  - { entity: pairing-request, effect: reads, facts: [Device name, Check code] }
  contexts:
    phone-joins:
      place: desktop::generate-qr-code
- text: "The Product pairs the two devices and introduces each to the other's paired devices"
  kind: product
  actor: user
  capability: accept-pairing-request
  entities:
  - { entity: pairing-request, effect: changes, from: Waiting, to: Accepted, facts: [] }
  - { entity: paired-device, as: phone, effect: creates, to: Paired, facts: [Name, Platform, Make and model, App version, Online, Last seen, Address, Requires PIN, Security key, Position] }
  - { entity: paired-device, as: computer, effect: creates, to: Paired, facts: [Name, Platform, Make and model, App version, Online, Last seen, Address, Requires PIN, Security key, Position] }
  - { entity: pairing-code, effect: changes, from: Broadcasting, to: Used, facts: [Time left] }
  contexts:
    phone-joins:
      place: desktop::generate-qr-code
---

# Pair a phone with a computer

## Trigger

The User wants their phone and computer to work together.

## Outcome

The phone and the computer are paired, after the User confirmed the same check code on both screens.
