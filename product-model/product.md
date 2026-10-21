---
id: fileapex
summary: A local-first file manager and sharing hub for Android, macOS, Windows and Linux. Pair your own
  devices once, then move files, share the clipboard, post to a shared Bulletin Board and see a phone's
  notifications on a computer, directly over your network.
category: file-sharing
tags:
- file-transfer
- clipboard
- android
- desktop
- kotlin-multiplatform
authors:
- name: ByHowieCreations
  url: https://github.com/byhowiecreations
license: MIT
languages:
- en
- es
- zh-CN
limitations:
- Files, clipboard text, Bulletin Board messages and notifications go only between devices the User has paired; there are no accounts and no FileApex server in the middle.
- Anything that reaches over the internet (a Google account with Drive Relay, Tailscale, Iroh) is something the User turns on; without it, devices meet on the local network.
- Clipboard sharing carries text and links, not images or files.
- A phone shares its notifications only from Android, only from the apps the User turns on, and only with one paired device; the receiving device keeps them in memory and never stores them.
- FileApex runs on Android, macOS, Windows and Linux; iPhone and iPad are not supported.
references:
- {kind: doc, role: intent, target: README.md}
- {kind: doc, role: intent, target: PRIVACY.md}
- {kind: doc, role: context, target: screenshots.md}
- {kind: code, role: implementation, target: composeApp/src/commonMain/kotlin/com/fileapex/App.kt}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/navigation/AppRoute.kt}
---

# FileApex

FileApex links a person's own phones and computers into one paired group. Two devices pair once by comparing a code on both screens, and every device already paired with either side joins in. From then on the User browses another device's folders, sends files and folders to several devices at once, sends the clipboard, posts messages and files to a Bulletin Board every device shares, and, on a computer, reads and answers the phone's notifications. A send to a device that cannot be reached waits in Queued Files until it can.

## Intent

**A local-first file manager and sharing hub. Browse, send and sync between your own devices without a cloud in the middle.**

Pair your phone, Mac and PC once, then move files, share the clipboard, send messages and see your phone's notifications from any of them. Files go straight between your devices over your network. Anything that touches the internet is opt-in.
