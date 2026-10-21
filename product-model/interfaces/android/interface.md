---
type: mobile-app
actors:
- user
references:
- {kind: code, role: implementation, target: composeApp/src/androidMain/kotlin/com/fileapex/MainActivity.kt}
- {kind: code, role: implementation, target: composeApp/src/androidMain/kotlin/com/fileapex/BulletinShareActivity.kt}
- {kind: code, role: implementation, target: composeApp/src/androidMain/kotlin/com/fileapex/ClipboardPushTileService.kt}
- {kind: code, role: implementation, target: composeApp/src/commonMain/kotlin/com/fileapex/App.kt}
---

# FileApex for Android

The Android app, from Google Play or the GitHub release. Besides its own screens it is reached from the system Share sheet (Send with FileApex, a Direct Share shortcut per paired device, Post to Bulletin Board), from the Send clipboard quick-settings tile and from the buttons on its Server Active notification.
