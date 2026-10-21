---
appliesTo:
- type: capability
  id: rename-device
- type: entity
  id: device-settings
  effect: changes
  facts: [Device name]
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/device/DeviceNameCoordinator.kt#DeviceNameCoordinator
---

# A device name is letters and numbers, with spaces and hyphens

A name that is empty or holds any other character is refused, on this device and when another device renames it.
