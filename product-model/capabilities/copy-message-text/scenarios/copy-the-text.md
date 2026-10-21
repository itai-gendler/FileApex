---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User swipes a message open and chooses Copy to clipboard"
  kind: actor
  actor: user
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Text] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product puts the text on this device's clipboard and says it was copied"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
---

# Copy the text

## Trigger

The User wants to paste a posted text or link elsewhere.

## Outcome

The text is on the clipboard.
