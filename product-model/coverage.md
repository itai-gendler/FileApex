---
scope: FileApex's pairing, file browsing and transfer, clipboard, Bulletin Board and phone notification workflows on Android and desktop, with the settings that govern them.
method: Static reading of the tracked Kotlin Multiplatform sources, macOS extensions and documentation at the pinned commit.
covered:
  - description: Pairing codes, pairing requests, introductions and removals across the group.
    paths: [shared/src/commonMain/kotlin/com/fileapex/domain/pairing/, shared/src/commonMain/kotlin/com/fileapex/security/IdentityBinding.kt, shared/src/commonMain/kotlin/com/fileapex/security/PeerIntroductions.kt, shared/src/commonMain/kotlin/com/fileapex/presentation/GenerateQrViewModel.kt, shared/src/commonMain/kotlin/com/fileapex/ui/GenerateQrScreen.kt, shared/src/commonMain/kotlin/com/fileapex/ui/PairingQrPanel.kt, shared/src/commonMain/kotlin/com/fileapex/ui/JoinDeviceScreen.kt]
  - description: Paired device records, names, order and the Devices page.
    paths: [shared/src/commonMain/kotlin/com/fileapex/data/device/, shared/src/commonMain/kotlin/com/fileapex/data/db/, shared/src/commonMain/kotlin/com/fileapex/domain/device/DeviceNameCoordinator.kt, shared/src/commonMain/kotlin/com/fileapex/domain/device/DeviceOrderCoordinator.kt, shared/src/commonMain/kotlin/com/fileapex/presentation/DevicesViewModel.kt, shared/src/commonMain/kotlin/com/fileapex/presentation/devices/, shared/src/commonMain/kotlin/com/fileapex/presentation/DeviceListRow.kt, shared/src/commonMain/kotlin/com/fileapex/ui/DevicesScreen.kt, shared/src/commonMain/kotlin/com/fileapex/ui/devices/]
  - description: The peer-to-peer server routes every device answers.
    paths: [shared/src/commonMain/kotlin/com/fileapex/network/routes/, shared/src/commonMain/kotlin/com/fileapex/network/FileApexServer.kt, shared/src/commonMain/kotlin/com/fileapex/session/]
  - description: File browsing, preview, copy and paste, remote delete and the explorer screens.
    paths: [shared/src/commonMain/kotlin/com/fileapex/presentation/ExplorerViewModel.kt, shared/src/commonMain/kotlin/com/fileapex/presentation/explorer/, shared/src/commonMain/kotlin/com/fileapex/domain/browse/, shared/src/commonMain/kotlin/com/fileapex/data/files/, shared/src/commonMain/kotlin/com/fileapex/data/clipboard/, shared/src/commonMain/kotlin/com/fileapex/ui/explorer/, shared/src/commonMain/kotlin/com/fileapex/ui/FileExplorerScreen.kt]
  - description: Sending, the transfer queue and the share-sheet pickers.
    paths: [shared/src/commonMain/kotlin/com/fileapex/domain/transfer/, shared/src/commonMain/kotlin/com/fileapex/data/transfer/, shared/src/commonMain/kotlin/com/fileapex/presentation/TransferQueueViewModel.kt, shared/src/commonMain/kotlin/com/fileapex/presentation/ShareSendViewModel.kt, shared/src/commonMain/kotlin/com/fileapex/ui/TransferQueueScreen.kt, shared/src/commonMain/kotlin/com/fileapex/ui/ShareSendScreen.kt, macos/ShareExtension/, macos/Shared/, macos/Tray/]
  - description: Clipboard sharing and its settings.
    paths: [shared/src/commonMain/kotlin/com/fileapex/domain/clipboard/, shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsClipboardPage.kt, shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsClipboardShareTargetsPage.kt, composeApp/src/androidMain/kotlin/com/fileapex/ClipboardPushTileService.kt, composeApp/src/androidMain/kotlin/com/fileapex/ClipboardPushActivity.kt]
  - description: The Bulletin Board, its sync between devices and battery alerts.
    paths: [shared/src/commonMain/kotlin/com/fileapex/data/bulletin/, shared/src/commonMain/kotlin/com/fileapex/data/note/, shared/src/commonMain/kotlin/com/fileapex/presentation/NotesViewModel.kt, shared/src/commonMain/kotlin/com/fileapex/ui/notes/, shared/src/commonMain/kotlin/com/fileapex/platform/BatteryBulletinPolicy.kt, shared/src/androidMain/kotlin/com/fileapex/platform/BatteryBulletinCoordinator.kt, macos/BulletinShareExtension/, composeApp/src/androidMain/kotlin/com/fileapex/BulletinShareActivity.kt]
  - description: Phone notification sharing, the Simple layout Home and the notification settings.
    paths: [shared/src/commonMain/kotlin/com/fileapex/domain/notifications/, shared/src/commonMain/kotlin/com/fileapex/ui/adaptive/, shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsBroadcastNotificationsPage.kt, shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsNotificationsPage.kt, shared/src/androidMain/kotlin/com/fileapex/platform/FileApexNotificationListenerService.kt]
  - description: PIN, device name, remote file deletion and leave-and-wipe settings.
    paths: [shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsPinRequiredPage.kt, shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsDeviceNamePage.kt, shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsRemoteFileDeletionPage.kt, shared/src/commonMain/kotlin/com/fileapex/ui/SecurityAccountScreen.kt, shared/src/commonMain/kotlin/com/fileapex/domain/reset/, shared/src/commonMain/kotlin/com/fileapex/data/settings/]
  - description: App shell and dialogs shared by every screen.
    paths: [composeApp/src/commonMain/kotlin/com/fileapex/App.kt, shared/src/commonMain/kotlin/com/fileapex/navigation/]
exclusions:
  - description: Build, signing, packaging and release tooling.
    paths: [build.gradle.kts, settings.gradle.kts, gradle/, gradlew, gradlew.bat, gradle.properties, gradle.user.properties.example, signing.local.env.example, scripts/, fastlane/, linux/, macos/scripts/, macos/launcher.uuid, macos/FileApexExtensions.xcodeproj/, .githooks/, .gitattributes, .gitignore, version.md]
  - description: Themes, icons, layouts and other visual design.
    paths: [shared/src/commonMain/kotlin/com/fileapex/ui/theme/, shared/src/commonMain/kotlin/com/fileapex/ui/kinetic/, shared/src/commonMain/kotlin/com/fileapex/ui/BulletinBoardStyleRenderer.kt, shared/src/commonMain/kotlin/com/fileapex/data/settings/AppTheme.kt, shared/src/commonMain/kotlin/com/fileapex/data/settings/ThemeTraits.kt, shared/src/commonMain/composeResources/drawable/, icon/]
  - description: Tests and test fixtures.
    paths: [shared/src/desktopTest/, shared/src/androidUnitTest/]
  - description: Translations of the interface text.
    paths: [shared/src/commonMain/composeResources/files/i18n/, shared/src/androidMain/assets/i18n/, shared/src/desktopMain/resources/i18n/]
  - description: Bundled licence texts.
    paths: [THIRD_PARTY_LICENSES.md, LICENSE, shared/src/androidMain/assets/legal/, shared/src/desktopMain/resources/legal/]
unmapped:
  - description: The command line and terminal dashboard on desktop.
    paths: [shared/src/desktopMain/kotlin/com/fileapex/cli/, windows/bin/]
  - description: The browser extension and the browser share page it talks to.
    paths: [browser-extension/]
  - description: The always-on Docker node and its embedded Tailscale daemon.
    paths: [Dockerfile, DOCKER.md, native/]
  - description: Tailscale and Iroh remote access settings and transports.
    paths: [shared/src/commonMain/kotlin/com/fileapex/tailscale/, shared/src/commonMain/kotlin/com/fileapex/iroh/, shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsTailscalePage.kt, shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsIrohPage.kt]
  - description: Google account linking, cloud presence and Google Drive Relay setup, sync and clean-up.
    paths: [shared/src/commonMain/kotlin/com/fileapex/cloud/, shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsGoogleAccountPage.kt]
  - description: Device Details, battery checks and Locate Phone.
    paths: [shared/src/commonMain/kotlin/com/fileapex/domain/diagnostics/, shared/src/commonMain/kotlin/com/fileapex/domain/device/PhoneLocator.kt, shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsDeviceDetailsPage.kt, shared/src/commonMain/kotlin/com/fileapex/ui/BatteryTerminalOverlay.kt]
  - description: Presence, wake signals and background keep-alive of the share server.
    paths: [shared/src/commonMain/kotlin/com/fileapex/domain/presence/, shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsBackgroundPersistencePage.kt, shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsAutoLaunchPage.kt]
  - description: Security key confirmation prompts after a device's key changes.
    paths: [shared/src/commonMain/kotlin/com/fileapex/security/tls/]
  - description: Backup & Sync of folders to another device.
    paths: [shared/src/commonMain/kotlin/com/fileapex/domain/backup/, shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsBackupPage.kt]
  - description: Local file management tools (rename, move, compress, favorites, Trash, storage analysis).
    paths: [shared/src/commonMain/kotlin/com/fileapex/ui/tools/, shared/src/commonMain/kotlin/com/fileapex/ui/StorageToolsScreen.kt]
  - description: In-app updates, including updates shared on the Bulletin Board.
    paths: [shared/src/commonMain/kotlin/com/fileapex/update/, shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsCheckForUpdatesPage.kt]
  - description: Onboarding, permissions, language choice, demo mode and feedback.
    paths: [shared/src/commonMain/kotlin/com/fileapex/ui/OnboardingScreen.kt, shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsOnboardingPermissionsPage.kt, shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsLanguagePage.kt, shared/src/commonMain/kotlin/com/fileapex/domain/demo/]
limitations: []
---

# Coverage
