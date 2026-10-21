---
entities:
- entity: paired-device
  shows:
  - Name
  - Make and model
  - Online
- entity: device-settings
  shows:
  - Connected device
  collects:
  - Connected device
- entity: phone-notification
  shows:
  - Category
  - App
  - From
  - Title
  - Text
  - Can reply
  - Posted at
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/adaptive/SimpleHome.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/adaptive/simple/SimpleOverview.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/adaptive/simple/SimpleNotifications.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/adaptive/SimpleNotificationList.kt
---

# Home

Home in the Simple layout: the one connected device, its make, battery and storage, whether clipboard sharing is on, and the connected phone's notifications counted as Messages, Emails and Other Notifications, each list opening to its conversations.
