---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User picks a filter: Links, Images, Documents, Snippets, Files, Pinned or a hashtag"
  kind: actor
  actor: user
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Kind, Locked] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product shows only the matching messages; filters with nothing to show are not offered"
  kind: product
  actor: user
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Text, Kind, Attachment name, Locked] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
---

# Filter the board

## Trigger

The board is long and the User is after one kind of post.

## Outcome

Only matching messages are listed; Snippets are short texts without links, Pinned are the locked ones.
