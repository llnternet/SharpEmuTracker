# SharpEmu Tracker

Distribution repo for **SharpEmu Tracker**, an unofficial Android companion app that displays
the build/CI status of the [SharpEmu](https://github.com/sharpemu/sharpemu) project's public
GitHub Actions runs.

Grab the latest APK from [Releases](https://github.com/llnternet/SharpEmuTracker/releases).

## 🖥️ Using this on Windows

This app is Android-only (view-only, no downloading/installing builds). If you're on Windows and
want to actually download and install SharpEmu builds, see
**[SharpEmu Updater](https://github.com/llnternet/SharpEmuUpdater)** -- the full desktop companion
app.

## ⚠️ Disclaimer

This is an independent, unofficial project. The developer of SharpEmu Tracker is **not
affiliated with, endorsed by, or associated with**:

- the SharpEmu project or its maintainers/contributors, or
- Sony Interactive Entertainment Inc., or any of its affiliates.

"PlayStation," "PS5," and related marks are trademarks of Sony Interactive Entertainment Inc.
Any reference to them here is solely to describe compatibility/context and does not imply any
sponsorship or endorsement. This app contains no PlayStation firmware, BIOS, system software, or
game data of any kind, and it does not run, execute, or emulate anything -- it only displays
public build/CI status from GitHub. Provided "as is," without warranty of any kind.

## ✨ Features

**📦 Build Tracking**
- Tracks any fork/branch on GitHub -- switch anytime via "Switch Fork" with search
- Classifies builds the same way as the desktop app: Success / Regression / Still Failing /
  In Progress / Queued / Needs Approval / Cancelled / Skipped
- Shows which platforms (Windows/macOS/Linux) each build produced artifacts for
- Tap any build to open it on GitHub in your browser
- Only re-checks the list when GitHub's Actions page actually has something new -- no flicker,
  no wasted API calls from switching tabs or reopening the app
- Cancelled/skipped builds with no actual Windows artifact are filtered out automatically --
  same as desktop, since SharpEmu itself only builds for Windows
- Automatically keeps following the tracked repo if it's ever renamed or transferred on GitHub
- Background build notifications stay current for the active fork/branch and never repeat for
  the same build

**🔔 Notifications & Status**
- Background notifications for new builds even while the app is closed (Android enforces a
  15-minute minimum check interval)
- Background notifications when a new version of this app itself is available, even while
  the app is closed -- tap one to jump straight to that version's release notes
- Animated status icons matching GitHub's own Actions UI
- Live GitHub status indicator if GitHub itself is having an outage

**⚙️ Background Operation**
- Built to run in the background at all times so you don't miss a build or update
- Checks every 15 minutes by default -- the fastest Android allows without a persistent
  always-visible notification
- Opt in or out anytime in Settings -- turning it on requests the permissions needed for
  reliable background checks (notifications, battery-optimization exemption); turning it off
  cancels the background job entirely

**🎨 Interface**
- Dark purple theme matching SharpEmu's own branding
- Adapts to your screen size -- content stays a readable width on tablets instead of
  stretching edge-to-edge

**🔒 Security**
- Your GitHub token is encrypted at rest via the Android Keystore -- never stored as plain text
- Works with either classic or fine-grained Personal Access Tokens
- Token is sent only to `api.github.com` over HTTPS, never anywhere else, never logged

## 🐛 Recent Fixes

- Fixed a case where the app-update check could be silently skipped entirely on installs without
  a GitHub token saved (checking for the app's own updates never needed a token in the first
  place)
- The "app update available" notification now actually pops up as a heads-up banner with sound,
  instead of silently sitting in the status bar until you pulled down the notification shade
  yourself
- Default background check interval lowered from 30 to 15 minutes so update/build notifications
  land sooner (existing installs: change this in Settings, since it's a saved preference this
  update won't override for you)
- Platform labels no longer get cut off on narrower phones
- Platform labels now correctly disappear once that platform's artifact expires or is removed

## What this app does

SharpEmu Tracker reads public data from the GitHub Actions API for the SharpEmu project (and
any fork/branch you choose to follow) and displays build status, commit history, and available
platform artifacts in a simple mobile UI. That's it — it's a status viewer.

It does **not**:
- include, bundle, or distribute the SharpEmu emulator itself, or any of its build artifacts
- include, bundle, or distribute any PlayStation firmware, BIOS, system software, or game files
- run, execute, or emulate anything on your device
- modify, patch, or interact with SharpEmu's own source code or releases in any way
