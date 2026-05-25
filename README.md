# mkxp-z Android Reworked

[![Android Build](https://github.com/BookerRues9/mkxp-z-android-reworked/workflows/Android%20Build%20%26%20Release/badge.svg)](https://github.com/BookerRues9/mkxp-z-android-reworked/actions/workflows/android.yml)
[![GitHub release](https://img.shields.io/github/v/release/BookerRues9/mkxp-z-android-reworked)](https://github.com/BookerRues9/mkxp-z-android-reworked/releases)
[![GitHub downloads](https://img.shields.io/github/downloads/BookerRues9/mkxp-z-android-reworked/total)](https://github.com/BookerRues9/mkxp-z-android-reworked/releases)
[![GitHub stars](https://img.shields.io/github/stars/BookerRues9/mkxp-z-android-reworked?style=social)](https://github.com/BookerRues9/mkxp-z-android-reworked/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/BookerRues9/mkxp-z-android-reworked?style=social)](https://github.com/BookerRues9/mkxp-z-android-reworked/network/members)
[![GitHub issues](https://img.shields.io/github/issues/BookerRues9/mkxp-z-android-reworked)](https://github.com/BookerRues9/mkxp-z-android-reworked/issues)
[![Last Commit](https://img.shields.io/github/last-commit/BookerRues9/mkxp-z-android-reworked)](https://github.com/BookerRues9/mkxp-z-android-reworked/commits/main)
[![License](https://img.shields.io/github/license/BookerRues9/mkxp-z-android-reworked)](LICENSE)

Android port of [mkxp-z](https://github.com/mkxp-z/mkxp-z) focused on running RPG Maker XP games on Android devices.

---

## Overview

`mkxp-z Android Reworked` is an experimental Android port of the mkxp-z engine.  
The project aims to provide compatibility for RPG Maker XP games using native Android builds.

Although still experimental, many games are already playable.

---

## Project Information

| Component | Status |
|---|---|
| RPG Maker XP Support | ✅ |
| Android ARM64 | ✅ |
| Android ARMv7 | ✅ |
| OpenGL ES Rendering | ✅ |
| SDL Integration | ✅ |
| Ruby Runtime | ✅ |
| APK Builds | ✅ |
| 16KB Page Support | ⚠️ Experimental |

---

## Original Projects

| Project | Link |
|---|---|
| mkxp-z | https://github.com/mkxp-z/mkxp-z |
| Original Android Port | https://github.com/thehatkid/mkxp-z-android |

---

# Running mkxp-z on Android

## Installation Steps

| Step | Description |
|---|---|
| 1 | Install the APK on your Android device |
| 2 | Create the `mkxp-z` folder in internal storage |
| 3 | Copy your RPG Maker XP game files into the folder |
| 4 | Optional: configure `mkxp.json` |
| 5 | Launch the app and grant storage permissions |

Example storage path:
```txt
/storage/emulated/0/mkxp-z
```


# Build Guide

This section explains how to configure and build **mkxp-z Android Reworked** from source.

---

# Configuration

You can place a custom configuration file here:

```txt
app/jni/mkxp-z/mkxp.json
```

## Possible Uses

| Feature | Description |
|---|---|
| Custom Game Directory | Load games from custom storage paths |
| Script Preloading | Automatically preload Ruby scripts |
| External Storage Paths | Configure storage locations |
| Engine Tweaks | Modify engine behavior and settings |

---

# Build Environment

## Requirements

| Dependency | Version |
|---|---|
| Ubuntu | 22.04 |
| Android Studio | Latest |
| Android SDK | Installed |
| Android NDK | 23.2.8568313 |
| Ruby | 3.0+ |
| CMake | Installed |
| Build Tools | Installed |

---

# Environment Setup

## Install Dependencies

```bash
sudo apt update
sudo apt install build-essential cmake ruby-full
```

---

## Install RVM

```bash
sudo apt install curl gpg -y
curl -sSL https://get.rvm.io/ | bash
source ~/.rvm/scripts/rvm
```

---

## Install Ruby

```bash
rvm install 3.1
rvm use 3.1 --default
ruby -v
```

---

# Clone Repository

```bash
git clone https://github.com/BookerRues9/mkxp-z-android-reworked.git
cd mkxp-z-android-reworked/app/jni
```

---

# Download Dependencies

```bash
chmod +x get_deps.sh
./get_deps.sh
```

---

# Android Environment Variables

```bash
export ANDROID_HOME=/home/YOURUSER/Android/Sdk
export ANDROID_NDK_HOME=$ANDROID_HOME/ndk/23.2.8568313
export ARCH=linux-x86_64
export PATH=$ANDROID_NDK_HOME/toolchains/llvm/prebuilt/$ARCH/bin:$PATH
```

---

# Build Instructions

## ARMv7 Build

```bash
HOST=armv7a-linux-androideabi \
TARGET=arm-linux-androideabi \
ABI=armeabi-v7a \
make
```

---

## ARM64 Build

```bash
HOST=aarch64-linux-android \
TARGET=aarch64-linux-android \
ABI=arm64-v8a \
make
```

---

## Build Everything

```bash
make
```

---

# Android Studio

After compiling dependencies:

| Step | Action |
|---|---|
| 1 | Open the project in Android Studio |
| 2 | Sync Gradle |
| 3 | Build APK |
| 4 | Install on device |

---

# Known Issues

| Issue | Status |
|---|---|
| External SD save support on Android < 10 | ❌ |
| Windows MSYS2 Ruby extensions | ⚠️ |
| 16KB Android page support | Experimental |
| Some RPG Maker XP games | Partial compatibility |

---

# Roadmap

- Improve Android compatibility
- Modernize native toolchains
- Improve Ruby extension support
- Better performance
- Improve ARM64 support
- Investigate 16KB page compatibility

---

# Notes

- ARM64 builds are recommended for modern Android devices.
- Some RPG Maker XP games may require additional configuration.
- Android storage permissions may vary depending on Android version.
- Experimental support means some features may still be unstable.

---

Last updated: May 2026
