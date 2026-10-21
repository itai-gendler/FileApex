---
availability:
- { place: android }
- { place: desktop }
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/clipboard/ClipboardShareCoordinator.kt#ClipboardShareCoordinator
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/clipboard/ClipboardSharePolicy.kt#ClipboardSharePolicy
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/devices/DevicesClipboardActions.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerClipboardRoutes.kt
- kind: code
  role: implementation
  target: composeApp/src/androidMain/kotlin/com/fileapex/ClipboardPushTileService.kt
---

# Send the clipboard

Send the text or link on this device's clipboard to other paired devices, with Send Clipboard on Devices, Send clipboard on one device, the Android tile and notification button, or by copying while sending on its own is on. It is encrypted for each device, and a link opens in the receiving device's browser.
