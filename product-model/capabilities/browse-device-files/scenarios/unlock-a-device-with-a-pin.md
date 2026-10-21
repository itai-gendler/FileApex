---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User taps a device on Devices"
  kind: actor
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The device has Require PIN on and is not unlocked here"
  kind: condition
  entities:
  - { entity: paired-device, effect: reads, facts: [Requires PIN, Unlocked until] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product asks for the PIN for that device to browse files"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The User enters the PIN and chooses Unlock"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product opens the device and keeps it unlocked for the browse unlock idle timeout"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, effect: changes, facts: [Unlocked until] }
  - { entity: device-settings, effect: reads, facts: [Browse unlock idle timeout] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The Product lists the folders and files at its root"
  kind: product
  actor: user
  entities:
  - { entity: device-file, effect: reads, facts: [Name, Kind, Size, Date modified, Folder] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
---

# Unlock a device that asks for a PIN

## Trigger

The device being browsed protects its files with a PIN.

## Outcome

The device opens; it stays unlocked while the User keeps navigating, until the idle timeout or a return to the device list.

## Edge cases

- A wrong PIN is refused with "Incorrect PIN".
- When the unlock runs out mid-browse, the Product says the PIN session expired and asks for the PIN again.
