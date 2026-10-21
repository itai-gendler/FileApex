---
type: desktop-app
actors:
- user
references:
- {kind: code, role: implementation, target: composeApp/src/desktopMain/kotlin/com/fileapex/Main.kt}
- {kind: code, role: implementation, target: macos/ShareExtension/ShareViewController.swift}
- {kind: code, role: implementation, target: macos/BulletinShareExtension/BulletinShareViewController.swift}
- {kind: code, role: implementation, target: macos/Tray/TrayMenuView.swift}
- {kind: code, role: implementation, target: composeApp/src/commonMain/kotlin/com/fileapex/App.kt}
---

# FileApex for desktop

The app for macOS, Windows and Linux. On a Mac it is also reached from Finder and the system Share menu (Share with FileApex, Post to Bulletin Board) and from the menu bar, which lists the paired devices and sends dropped files to the ones selected.
