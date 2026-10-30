# Anvil — Releases & Downloads

[![Latest Release](https://img.shields.io/github/v/release/ccmscotland/Anvil-Releases?color=brightgreen&label=Latest%20Release)](https://github.com/ccmscotland/Anvil-Releases/releases/latest)
[![Platform](https://img.shields.io/badge/Platform-Android%20%7C%20Googlebook%20OS%20%7C%20DeX-blue)](https://github.com/ccmscotland/Anvil-Releases/releases/latest)
[![License](https://img.shields.io/badge/License-Proprietary-lightgrey)](https://github.com/ccmscotland/Anvil-Releases)

Anvil is a high-performance, keyboard-first code and text editor built specifically for Android, Android Laptop, and Googlebook OS. It adapts seamlessly from a compact phone layout to an expansive desktop workstation with multi-pane editing, extensive language grammars, and local/remote development storage.

---

## Download Latest APK

- **[Download Anvil v1.0.0 Release APK](https://github.com/ccmscotland/Anvil-Releases/releases/latest/download/Anvil-release.apk)** (14.5 MB, signed with RSA-4096 key, optimized)

All versions and historical release notes are available on the [Releases Page](https://github.com/ccmscotland/Anvil-Releases/releases).

---

## Highlights and Features

- **Adaptive Desktop Shell**:
  - Full desktop menu bar, split-view panes, tab strip with middle-click close, and draggable side panel.
  - Native multi-window support (`File -> New window` / `Ctrl+Alt+N`).
  - Support for Googlebook OS, Android 15-17 Desktop Mode, Samsung DeX, and ChromeOS ARC.
- **Voice Dictation with Rambler**:
  - Full compatibility with Googlebook OS Gemini-driven Rambler voice dictation and Gboard voice typing.
  - Context-aware thought-to-text rewrites utilizing surrounding document text and caret selection tracking.
  - Native shortcut passthrough (`Alt+D`, `Search+D`, dedicated hardware `Dictate` key `319`).
- **Precision Trackpad and Mouse Input**:
  - Two-finger touchpad scrolling with horizontal/vertical momentum.
  - `Ctrl + MouseWheel` / `Ctrl + Trackpad` editor font zooming (70%-250%).
  - System Drag and Drop to open files directly from the Files app.
- **30+ Syntax Highlighted Languages**:
  - Powered by TextMate grammars and Sora Editor: Python, Kotlin, JavaScript, TypeScript, Rust, Go, C/C++, Java, Shell, PowerShell, SQL, HTML, CSS, Markdown, YAML, JSON, TOML, Dockerfile, Makefile, Diff, and more.
- **Storage and Cloud Providers**:
  - Direct local Linux VM/host development folder paths (`/storage/emulated/10/Development`).
  - Android Storage Access Framework (SAF) with persisted permissions.
  - Remote sources: SMB, SFTP, FTP/FTPS, WebDAV, Google Drive, and GitHub branches.
- **Tools and Productivity**:
  - Command Palette (`Ctrl+Shift+P`), Quick Open (`Ctrl+P`), Find and Replace across files (`Ctrl+Shift+F`), Multi-cursor editing, Snippets, Line bookmarks, Markdown live preview (`Ctrl+Shift+\`), and JSON/XML formatting.
- **Model Context Protocol (MCP)**:
  - Built-in stdio/SSE MCP server allowing Claude, Cursor, Zed, and AI tools to read/write documentation and automate tests directly with Anvil.

---

## How to Install

### On Android and Android Tablets
1. Download `Anvil-release.apk` on your device.
2. Tap the downloaded file in your browser or file manager.
3. If prompted, grant permission to "Install unknown apps" for your browser/file manager.
4. Tap Install and open Anvil.

### On Googlebook OS / Android Laptop
1. Download `Anvil-release.apk` using Chrome.
2. Open the Files app and double-click the `.apk` file (or run `adb install -r Anvil-release.apk` from the Linux Terminal).
3. Confirm package installation.

---

## Release History

| Version | Release Date | Key Updates | Download |
|:---:|:---:|:---|:---:|
| v1.0.0 | October 2026 | Official 1.0.0 General Availability release. Full desktop shell, Googlebook OS Rambler Gemini voice dictation, RSA 4096-bit release signing, multi-window support. | [Release APK](https://github.com/ccmscotland/Anvil-Releases/releases/download/v1.0.0/Anvil-release.apk) |
| v0.70.3 | October 2026 | Googlebook OS Rambler Gemini voice dictation, IME selection synchronization, hardware dictation key passthrough, Save As integration. | [Release APK](https://github.com/ccmscotland/Anvil-Releases/releases/download/v0.70.3/Anvil-release.apk) |

---

## Feedback and Issues

Have a feature request, bug report, or idea for Anvil? Please submit them to the [Issues Tracker](https://github.com/ccmscotland/Anvil-Releases/issues).
