---
appliesTo:
- type: entity
  id: bulletin-message
  effect: removes
- type: capability
  id: view-bulletin-board
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/bulletin/BulletinBoardPolicy.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/bulletin/BulletinBoardRepository.kt
---

# The board keeps 90 days of unlocked messages

Unlocked messages older than 90 days are cleared from each device's board. A deleted message never comes back, even when a device that missed the delete sends it again.
