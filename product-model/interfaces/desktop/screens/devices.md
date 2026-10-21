---
entities:
- entity: paired-device
  shows:
  - Name
  - Platform
  - Online
  - Last seen
  - App version
  - Position
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/DevicesScreen.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/devices/DeviceCard.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/devices/DevicesActionBar.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/devices/DevicesDialogs.kt
---

# Devices

Every paired device with its platform, whether it is Ready or needs a tap to wake (with when it was last seen), and its app version, in the order the User set. From here the User adds a device, opens one to browse it, sends the clipboard, and renames, removes or reorders devices.
