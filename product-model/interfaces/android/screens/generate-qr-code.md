---
entities:
- entity: pairing-code
  shows:
  - Code
  - Device name
  - QR code
  - Time left
- entity: pairing-request
  shows:
  - Device name
  - Check code
  - Hint
- entity: paired-device
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/GenerateQrScreen.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/PairingQrPanel.kt
---

# Generate QR Code

The device waiting to be joined: its pairing code as a QR code and six digits, the minute left on the broadcast, and, when a device asks to join, that device with the check code to compare.
