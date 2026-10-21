---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The last code ran out"
  kind: condition
  entities:
  - { entity: pairing-code, as: old, effect: reads, facts: [Time left] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The User taps Retry"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The Product creates a different 6-digit code and broadcasts it for another minute"
  kind: product
  actor: user
  entities:
  - { entity: pairing-code, as: new, effect: creates, to: Broadcasting, facts: [Code, Device name, QR code, Time left] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
---

# Retry for a new code

## Trigger

The other device was not ready in time.

## Outcome

A new code is broadcasting; the old one stays Expired.
