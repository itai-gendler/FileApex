---
appliesTo:
- type: capability
  id: send-device-files
- type: capability
  id: view-queued-files
- type: entity
  id: queued-file
  effect: creates
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/transfer/TransferQueueCoordinator.kt#TransferQueueCoordinator
---

# Every send to another device goes through Queued Files

A send to another device is recorded in Queued Files before it starts and stays there until every device has it, so it outlives a closed app and goes out on its own when a device that was away is seen again. A device with no direct route is reached through Google Drive Relay when that is on.
