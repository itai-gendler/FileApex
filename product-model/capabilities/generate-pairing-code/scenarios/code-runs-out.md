---
kind: edge
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "A minute passes with no device confirming the code"
  kind: condition
  unattended: true
  entities:
  - { entity: pairing-code, effect: reads, facts: [Time left] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The Product stops the broadcast and ends the code"
  kind: product
  entities:
  - { entity: pairing-code, effect: changes, from: Broadcasting, to: Expired, facts: [Time left] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The Product says no device confirmed in time and offers Retry for a new QR code, code and broadcast"
  kind: product
  entities: []
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
---

# The code runs out unanswered

## Trigger

The code was shown but nobody joined within the minute.

## Outcome

The code is Expired and no longer accepted; Retry is offered.
