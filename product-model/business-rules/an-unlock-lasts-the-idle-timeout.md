---
appliesTo:
- type: capability
  id: browse-device-files
- type: entity
  id: paired-device
  effect: changes
  facts: [Unlocked until]
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/session/DeviceSessionManager.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/settings/PinIdleTimeout.kt
---

# A PIN unlock lasts until the idle timeout or the device list

After its PIN is entered, a device stays unlocked on this device for the browse unlock idle timeout after the last move in it (five minutes unless changed). Going back to the device list locks it again; with Immediate, nothing else keeps it unlocked.
