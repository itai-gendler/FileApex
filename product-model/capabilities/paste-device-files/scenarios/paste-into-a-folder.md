---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "Files are waiting to be pasted"
  kind: condition
  entities:
  - { entity: pending-copy, effect: reads, facts: [Files] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The User opens a folder on another device and chooses Paste here"
  kind: actor
  actor: user
  entities:
  - { entity: pending-copy, effect: reads, facts: [Files] }
  - { entity: device-file, as: folder, effect: reads, facts: [Name, Folder] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The Product copies the files into that folder, giving a numbered name to any that would replace a file there"
  kind: product
  actor: user
  entities:
  - { entity: device-file, as: pasted, effect: creates, facts: [Name, Kind, Size, Date modified, Folder] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The Product says where the files were pasted and refreshes the folder"
  kind: product
  actor: user
  entities:
  - { entity: device-file, as: pasted, effect: reads, facts: [Name, Folder] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
---

# Paste into a folder

## Trigger

The User wants the files in a particular folder.

## Outcome

The files are in the chosen folder; the pending copy stays for another paste.
