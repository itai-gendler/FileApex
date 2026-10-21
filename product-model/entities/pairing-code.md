---
domain: devices
references:
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/LanPairingDiscovery.kt#LanPairingDiscovery}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PairingBeacon.kt#PairingBeacon}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PairingPayload.kt}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/presentation/GenerateQrViewModel.kt#GenerateQrViewModel}
---

# Pairing code

The one-time code a device shows while it waits for another device to pair with it. A new code never repeats the previous one.

## Information kept

- **Code** — the 6-digit code.
- **Device name** — the name of the device showing it.
- **QR code** — the same code with the device's name and address, to scan instead of typing.
- **Time left** — how long the code is still broadcast to nearby devices.

## States

### Broadcasting

Shown on screen and announced on the local network so a nearby Join device screen can fill it in.

### Used

A device asked to pair with it, and the request was accepted or declined. The code takes no other request.

### Expired

The minute ran out with no device confirmed.
