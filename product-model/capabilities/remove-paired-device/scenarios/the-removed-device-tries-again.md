---
kind: edge
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The removed device still lists the device that removed it"
  kind: condition
  unattended: true
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The device that removed it refuses its requests"
  kind: product
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The removed device shows that the other device no longer recognizes it and must be paired again to rejoin"
  kind: product
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
---

# The removed device tries again

## Trigger

A removed device, which keeps its own data, reaches for a device that removed it.

## Outcome

Nothing is exchanged until the two devices pair again.
