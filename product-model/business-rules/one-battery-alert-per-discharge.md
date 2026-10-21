---
appliesTo:
- type: capability
  id: post-low-battery-alert
- type: entity
  id: bulletin-message
  effect: creates
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/platform/BatteryBulletinPolicy.kt#BatteryBulletinPolicy
- kind: code
  role: implementation
  target: shared/src/androidMain/kotlin/com/fileapex/platform/BatteryBulletinCoordinator.kt
---

# A phone posts one low battery alert per discharge

A phone posts a battery alert when it is at 15% or less and not charging, once until it has charged above 15% again, and withdraws its alerts from every board as soon as it is charging.
