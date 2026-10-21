---
kind: validation
routes:
  android: Android app
steps:
- text: "The User opens Local Files on a phone that has not granted all files access"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::local-files
- text: "The Product asks for all files access before it can list anything"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::local-files
---

# Grant file access first

## Trigger

Android has not given FileApex access to storage.

## Outcome

Local Files opens once access is granted.
