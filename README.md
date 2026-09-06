# 🎮 ReHLDS FakeBot Status

### Show YaPB bots with unique Steam2-style IDs in `status`

[![Build ReHLDS](https://github.com/cosminzm/rehlds-fakebot-status/actions/workflows/build.yml/badge.svg)](https://github.com/cosminzm/rehlds-fakebot-status/actions/workflows/build.yml)
[![GitHub release](https://img.shields.io/github/v/release/cosminzm/rehlds-fakebot-status)](https://github.com/cosminzm/rehlds-fakebot-status/releases)
[![GitHub stars](https://img.shields.io/github/stars/cosminzm/rehlds-fakebot-status)](https://github.com/cosminzm/rehlds-fakebot-status/stargazers)

A custom Linux i386 build of **ReHLDS 3.14.0.857** that modifies the `status` output so YaPB fake clients are displayed with randomly generated Steam2-style IDs instead of `BOT`.

---

## ✨ Features

- ✅ YaPB bots are no longer displayed as `BOT`
- ✅ Each bot receives a unique randomly generated Steam2-style ID
- ✅ IDs remain stable while the bot is connected
- ✅ IDs change when a new bot connection is created
- ✅ ReHLDS `3.14.0.857`
- ✅ Linux i386 `engine_i486.so`
- ✅ Standard and legacy-compatible builds
- ✅ YaPB and Reunion remain unchanged
- ✅ No AMX Mod X plugin required
- ✅ Fully automated GitHub Actions build

---

## 📋 Example

### Original ReHLDS

```text
# 1 "COSMIN"       1 STEAM_0:0:76086244
# 2 "VenomRaven"   2 BOT
# 3 "NightPhoenix" 3 BOT
# 4 "NightVenus"   4 BOT
# 5 "PhantomSable" 5 BOT
```

### With this build

```text
# 1 "COSMIN"       1 STEAM_0:0:76086244
# 2 "VenomNova"    2 STEAM_0:0:1977074823
# 3 "CrimsonSiren" 3 STEAM_0:0:805267073
# 4 "PhantomFury"  4 STEAM_0:1:1770740066
# 5 "DeathSting"   5 STEAM_0:0:1397812442
```

---

## 🛠️ How It Works

This project patches the **ReHLDS status formatting code** to change how YaPB fake clients are displayed by the `status` command.

Instead of:

```text
# 2 "BotName" 2 BOT
```

fake clients are displayed with a unique randomly generated Steam2-style ID:

```text
# 2 "BotName" 2 STEAM_0:0:1977074823
```

The generated IDs are used **only for displaying fake clients in the `status` command**.

### What This Project Does Not Modify

This project does **not** modify:

- YaPB
- Reunion
- AMX Mod X
- Steam authentication
- Player authentication
- Game server networking
- Player connections
- Server gameplay

No AMX Mod X plugin is required.

---

## 📥 Download

Ready-to-use compiled engines are available in the **Releases** section.

### Standard Build

```text
engine_i486.so
```

Recommended for servers running a modern Linux environment.

### Legacy Build

```text
engine_i486-legacy.so
```

The legacy build is compiled inside **Ubuntu 20.04 using GLIBC 2.31** and is intended for older Linux hosting environments.

If the standard build produces an error such as:

```text
GLIBC_2.32 not found
Unable to load engine, image is corrupt.
```

try the **legacy build**.

➡️ **[Download the latest release](../../releases/latest)**

---

## 📦 Release Files

| File | Description |
|---|---|
| `engine_i486.so` | Standard Linux i386 build |
| `engine_i486-legacy.so` | Legacy-compatible Linux i386 build using GLIBC 2.31 |

Both builds contain the same FakeBot Status modification.

The difference is the build environment and Linux/GLIBC compatibility.

---

## 🚀 Build

The project uses **GitHub Actions** to automatically compile the modified ReHLDS engine for Linux i386.

### Requirements

- GitHub account
- GitHub Actions enabled
- Counter-Strike 1.6 dedicated server
- ReHLDS Linux i386 server
- YaPB 4.x

### Build Steps

1. Open the **Actions** tab.
2. Select **Build patched ReHLDS i386**.
3. Click **Run workflow**.
4. Select the `main` branch.
5. Click **Run workflow** again.
6. Wait for the build to complete.
7. Open the successful workflow run.
8. Download the generated artifact.

The legacy artifact is named:

```text
engine_i486-fakebot-status-3.14.0.857-legacy
```

Inside the archive you will find:

```text
engine_i486.so
```

---

## 🎯 Server Installation

> ⚠️ **Always make a backup of your original `engine_i486.so` before replacing it.**

### Installation

1. Stop your Counter-Strike 1.6 server.
2. Locate the existing `engine_i486.so`.
3. Make a backup of the original file.
4. Choose the appropriate build from the Releases section.
5. Replace the original `engine_i486.so` with the downloaded build.
6. Keep your existing YaPB configuration unchanged.
7. Start the server.
8. Open the server console.
9. Run:

```text
status
```

### Expected Result

Instead of:

```text
# 2 "BotName" 2 BOT
```

you should see:

```text
# 2 "BotName" 2 STEAM_0:X:XXXXXXXXXX
```

Each fake client receives its own randomly generated Steam2-style ID.

---

## ⚙️ YaPB Configuration

The following YaPB settings should remain enabled:

```text
EnableFakeBotFeatures = 1
yb_enable_fake_steamids "1"
```

No YaPB source modification is required.

No AMX Mod X plugin is required.

---

## 🔄 Reverting to the Original Engine

If the server does not start correctly after installing the modified engine:

1. Stop the server.
2. Remove the modified `engine_i486.so`.
3. Restore your original backup.
4. Start the server again.

Always keep a backup of the original ReHLDS engine.

---

## 🧪 Tested Environment

The modification has been tested with:

| Component | Version |
|---|---|
| ReHLDS | 3.14.0.857 |
| Platform | Linux i386 |
| Engine | `engine_i486.so` |
| YaPB | 4.x |
| Game | Counter-Strike 1.6 |

### Test Result

```text
# 1 "COSMIN"       1 STEAM_0:0:76086244
# 2 "VenomNova"    2 STEAM_0:0:1977074823
# 3 "CrimsonSiren" 3 STEAM_0:0:805267073
# 4 "PhantomFury"  4 STEAM_0:1:1770740066
# 5 "DeathSting"   5 STEAM_0:0:1397812442
```

The legacy-compatible build has also been successfully tested on a Linux game server using GLIBC 2.31.

---

## 📌 Compatibility

| Component | Version |
|---|---|
| ReHLDS | 3.14.0.857 |
| Platform | Linux i386 |
| Engine | `engine_i486.so` |
| YaPB | 4.x |
| AMX Mod X | Compatible |
| Reunion | Compatible |
| Counter-Strike 1.6 | Compatible |

> Compatibility depends on the Linux environment and GLIBC version provided by the hosting provider.

---

## ⚠️ Disclaimer

The Steam2-style IDs generated by this project are **not real Steam accounts** and are **not used for Steam authentication**.

They are generated solely for displaying fake clients in the `status` command.

This modification does not provide fake Steam authentication and does not turn YaPB bots into authenticated Steam players.

---

## 📦 Releases

Stable versions are published through the GitHub **Releases** section.

Each release can include:

```text
engine_i486.so
engine_i486-legacy.so
```

For development or testing builds, use the GitHub Actions artifacts.

---

## 📝 Changelog

### v1.0.0

- Added ReHLDS 3.14.0.857 support
- Added Steam2-style IDs for YaPB fake clients
- Added randomly generated IDs
- Added Linux i386 `engine_i486.so`
- Added legacy-compatible build using GLIBC 2.31
- Added automated GitHub Actions build
- Added installation and rollback instructions
- Added standard and legacy download options

---

## 🐛 Bug Reports

If you encounter a problem, please include:

- ReHLDS version
- YaPB version
- Operating system
- Server console output
- `status` output
- Relevant error messages

Please open an **Issue** with as much information as possible.

---

## 🤝 Contributing

Suggestions, bug reports and improvements are welcome.

Feel free to open an **Issue** or submit a **Pull Request**.

---

## ❤️ Credits

- **ReHLDS** — Re-engineered Half-Life Dedicated Server
- **YaPB** — Yet Another POD-Bot
- **AMX Mod X**
- **Reunion**
- **GitHub Actions**

---

### ⭐ If this project is useful to you, consider giving the repository a star!
