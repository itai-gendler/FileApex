---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Add New Device, then Generate QR Code"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product starts the share server and creates a fresh 6-digit code, never the one it used last"
  kind: product
  actor: user
  entities:
  - { entity: pairing-code, effect: creates, to: Broadcasting, facts: [Code, Device name, QR code, Time left] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The Product announces the code on the local network several times a second so a nearby Join device screen can fill it in"
  kind: product
  actor: user
  entities:
  - { entity: pairing-code, effect: reads, facts: [Code, Device name] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The QR code, the six digits and the time left stay on screen while the minute runs"
  kind: condition
  entities:
  - { entity: pairing-code, effect: reads, facts: [Code, QR code, Time left] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
---

# Show a QR code and six digits

## Trigger

The User wants to add a phone or computer to their devices.

## Outcome

A pairing code is broadcasting for one minute, ready for the other device to join with.
