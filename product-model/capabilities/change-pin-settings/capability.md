---
availability:
- { place: android }
- { place: desktop }
domain: security-and-access-control
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsPinRequiredPage.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/settings/PinIdleTimeout.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/FileApexServer.kt
---

# Change PIN settings

In Settings → PIN required, require other devices to enter this device's PIN to pair and to browse it, set the 4 to 8 digit PIN, and choose how long a PIN-protected device stays unlocked while this device browses it.
