---
entities:
- entity: device-settings
  shows:
  - Require PIN
  - Device PIN
  - Browse unlock idle timeout
  collects:
  - Require PIN
  - Device PIN
  - Browse unlock idle timeout
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsPinRequiredPage.kt
---

# PIN required

Settings → PIN required: whether other devices need this device's PIN, the PIN itself, and how long a browsed device stays unlocked.
