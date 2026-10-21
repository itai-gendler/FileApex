---
references:
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/ui/DevicesScreen.kt}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/presentation/DevicesViewModel.kt}
---

# Devices

The Devices page and Add New Device: who is paired, pairing new devices, renaming, reordering and removing them, and opening one to browse it.

## Boundary

This domain does not own what is sent to a device once it is open (files, clipboard) or the device's own settings.
