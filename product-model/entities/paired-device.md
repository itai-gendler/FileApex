---
domain: devices
references:
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/data/db/FileApexDatabase.kt#PairedDeviceEntity}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/data/device/DeviceRepository.kt}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/presentation/DeviceListRow.kt}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/domain/device/DeviceOrderCoordinator.kt}
---

# Paired device

Another phone or computer this device has paired with. Each device keeps its own record of every other one, and the records stay in step across the group: a device added or removed on one is added or removed on the others.

## Information kept

- **Name** — what the device is called on the Devices list, the Bulletin Board and every picker.
- **Platform** — Android, macOS, Windows, Linux, or a Docker node.
- **Make and model** — the hardware it reports.
- **App version** — the FileApex version it runs.
- **Online** — whether it answers right now: Ready, or Tap to wake when it does not.
- **Last seen** — when it last answered, shown while it is offline.
- **Address** — where on the network it was last reached.
- **Requires PIN** — whether it asks for its PIN before pairing or browsing.
- **Unlocked until** — how long this device may keep browsing it after its PIN was entered.
- **Security key** — the key the check code was compared against when the two devices paired.
- **Position** — its place in this device's order of the Devices list.

## States

### Paired

Listed on the Devices list and reachable for every exchange.

### Removed

Taken off the list on every device. It stays gone until it is paired again.
