---
availability:
- { place: android }
- { place: desktop }
domain: bulletin-board
references:
- kind: code
  role: implementation
  target: shared/src/androidMain/kotlin/com/fileapex/platform/BatteryBulletinCoordinator.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/platform/BatteryBulletinPolicy.kt#BatteryBulletinPolicy
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/data/note/NoteRepository.kt#NoteRepository
---

# Post a low battery alert

An Android phone posts a battery alert to every board when it drops to 15% while not charging, and withdraws it from every board once it charges.
