---
kind: validation
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User taps a large image or text file"
  kind: actor
  actor: user
  entities:
  - { entity: device-file, effect: reads, facts: [Name, Size] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The file is over the preview size, or its size is unknown"
  kind: condition
  entities:
  - { entity: device-file, effect: reads, facts: [Size] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The Product says the file is too large to preview and fetches nothing"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
---

# Too large to preview

## Trigger

The file is too big to show.

## Outcome

No preview; the file can still be downloaded.
