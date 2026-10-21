---
entities:
- entity: pairing-code
  shows:
  - Code
  - Device name
  collects:
  - Code
- entity: pairing-request
  shows:
  - Check code
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/JoinDeviceScreen.kt
---

# Join device

Where the joining device takes a pairing code: filled in from a nearby broadcast, typed, or scanned on Android, then the check code to compare and, when the other device asks for one, its PIN.
