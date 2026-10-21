---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Delete on files in another device's folders"
  kind: actor
  actor: user
  entities:
  - { entity: device-file, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The User confirms \"Delete on the other device?\""
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The Product has the other device move the files to its Trash"
  kind: product
  actor: user
  entities:
  - { entity: device-file, effect: removes }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The Product says they were deleted and refreshes the folder"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
---

# Delete after confirming

## Trigger

A file on another device is no longer wanted.

## Outcome

The files are gone from the folder and sit in that device's Trash.

## Edge cases

- If one of several files fails, the folder is refreshed so it shows what the device really has.
