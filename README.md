# ⚡ Yoda Bot v2.0 — Official Releases & Distribution

[![Release](https://img.shields.io/badge/Release-v2.0.0-gold?style=for-the-badge&logo=github)](https://github.com/arthurliszkievich/yodabot-releases/releases/tag/v2.0.0)
[![Platforms](https://img.shields.io/badge/Platforms-Windows%20%7C%20Linux%20%7C%20Android-blue?style=for-the-badge)](https://github.com/arthurliszkievich/yodabot-releases/releases/tag/v2.0.0)
[![License](https://img.shields.io/badge/License-Proprietary-red?style=for-the-badge)](https://github.com/arthurliszkievich/yodabot-releases)

Welcome to the official distribution repository for **Yoda Bot v2.0**, the premier high-performance automation suite and box management engine for *Dragon Ball Z: Dokkan Battle* (Global & Japan).

---

## 📦 Direct Download Links (Release `v2.0.0`)

Download the release package designed specifically for your operating system:

| Platform / Component | Architecture / Format | Direct Download Link | Description |
| :--- | :--- | :--- | :--- |
| **Windows Desktop** | `x64` (`.zip`) | [📥 **yodabot_2.0_windows.zip**](https://github.com/arthurliszkievich/yodabot-releases/releases/download/v2.0.0/yodabot_2.0_windows.zip) | Standalone package for Windows 10 & 11. Includes double-click `Launch_Windows.py` with automatic SAC/MOTW unblock and Python 3.12 installer. |
| **Android / Termux** | `ARM64` (`.zip`) | [📥 **yodabot_2.0_mobile.zip**](https://github.com/arthurliszkievich/yodabot-releases/releases/download/v2.0.0/yodabot_2.0_mobile.zip) | Mobile package for Android via Termux ARM64. Includes zero-friction `mobile_setup.sh` and global `yoda` command. |
| **Linux Desktop** | `x86_64` (`.zip`) | [📥 **yodabot_2.0_linux.zip**](https://github.com/arthurliszkievich/yodabot-releases/releases/download/v2.0.0/yodabot_2.0_linux.zip) | High-speed native Cython-compiled `.so` build for Ubuntu, Debian, Fedora, and Arch Linux x64. |
| **Google Auth Helper** | `Android APK` (`.apk`) | [📥 **yoda-auth-helper.apk**](https://github.com/arthurliszkievich/yodabot-releases/releases/download/v2.0.0/yoda-auth-helper.apk) | Dedicated Android companion app that intercepts Google OAuth callbacks, enabling 100% automated Google login in Termux. |

---

## 📖 Official Guides & Documentation

Comprehensive step-by-step installation, authentication, and feature manuals are available below:

- 📖 **[Complete Command Reference (COMMANDS.md)](./COMMANDS.md)**
  - Comprehensive reference of all CLI commands and parameters.
  - Golden Rule of Navigation: Double Enter (`2x Enter`) instant menu return.
  - Farming suites (`omega_farm`, `db_story_all`, `kagi`, `eza_run`).
  - Mission batch claiming (`mission`, `auto_mission`).
  - Team builder (`smart_team`), Ultimate Clash (`clash`), and box cleaner (`clean_box`).
  - APEX Web GUI feature walkthrough and 1-click workflows.

- 🖥️ **[Desktop Guide (Windows 10/11 & Linux x64)](./README_DESKTOP.md)**
  - Windows double-click setup & Smart App Control bypass.
  - Linux launchers (`launch_linux.sh` & `start_gui.sh`).
  - Discord OAuth verification & Google Auto-Login via Chrome DevTools Protocol (CDP).
  - Interactive APEX Web GUI walkthrough.

- 📱 **[Mobile Guide (Android Termux & Yoda Auth Helper APK)](./README_MOBILE.md)**
  - Installing Termux, Termux:API, and `yoda-auth-helper.apk`.
  - Zero-friction automated setup script (`mobile_setup.sh`).
  - Touchscreen Web GUI on Android (`http://127.0.0.1:8080`).
  - Google account linking and mobile troubleshooting.

---

## 🌟 What's New in v2.0.0

- 🚀 **Full APEX Interactive Web GUI**: Browser interface (`http://127.0.0.1:8080`) with card sorting, instant filters, 1-Click Level & SA Max, 1-Click 100% Hidden Potential, and step-by-step Dokkan Awakening with in-browser stamina refill popups.
- 🛡️ **Native Browser Google Auto-Login (CDP)**: Direct Chromium WebSocket automation for Google login—no ChromeDriver downloads, selenium-wire, or proxy configurations needed on Desktop.
- 📲 **Android Companion Helper**: `yoda-auth-helper.apk` enables 100% automated Google login on Android Termux.
- 🔄 **Game Version Auto-Update**: Self-healing engine that detects new Dokkan Battle client versions and updates hashes dynamically.
- ⚡ **Dedicated OS Packaging**: Strictly clean builds with zero cross-platform script pollution and fully compiled in-RAM GUI vaults.

---

## 💬 Community & Support

Join the official Yoda Community on Discord for roles, news, updates, and discussion.

