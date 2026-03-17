<!-- >[!WARNING]
> **🌅 PROJECT ARCHIVED**  
> This journey has reached its end. The repository is now archived and will no longer receive updates.  
>[The final stable release remains available here](https://github.com/debuggerdragon311/zedx-appimage/releases/tag/v0.223.4)
-->

# 🌅 ZedX AppImage: A Final Farewell

[![Zed](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/zed-industries/zed/main/assets/badge/v0.json)](https://zed.dev)
[![Status: Archived](https://img.shields.io/badge/Status-Archived-red.svg)]()
[![License: AGPL-3.0](https://img.shields.io/badge/License-AGPL--3.0-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)

> *"There is a season for every line of code, and a twilight for every project."*

## 🍂 The Sun Sets on ZedX

I started ZedX AppImage with a simple, quiet dream: to capture lightning in a bottle. I wanted to bring the blazing-fast brilliance of the Zed editor to every Linux machine—unbound by package managers, untethered by dependencies, and free to run anywhere. For a beautiful stretch of time, together, we made that spark a reality. 

But like all journeys, this one has reached its final destination. 

The winds of creativity are calling me toward new horizons and different projects. Time—the most unyielding compiler of all—has left me with too few hours to give this repository the dedication, love, and maintenance it truly deserves. Rather than letting it slowly fade into obsolescence, I choose to close this chapter here, archiving the project with the pride of what we built.

To everyone who downloaded a build, reported a glitch in the matrix, or simply believed in the magic of a truly portable editor—**thank you**. You breathed life into these binaries. It has been a profound honor to serve you and the broader Linux community.

The code remains, the final releases are still hosted, and the open-source spirit endures. If you wish to carry the torch, you are more than welcome to fork this repository and build upon the foundation left behind. 

Until our paths cross in another repository, keep coding, keep creating, and keep the open-source spirit alive.

With deep gratitude,<br>
**@debuggerdragon311**

---

### 📌 What This Means
- **No further updates:** This repository is officially archived.
- **Final Release:** You can still download the[last stable build (v0.223.4)](https://github.com/debuggerdragon311/zedx-appimage/releases/tag/v0.223.4).
- **Official Alternatives:** Please transition to the official [Zed Editor](https://zed.dev) releases for future updates, security patches, and features.
- **Forking:** The source code and build scripts remain available under the AGPL-3.0 license for anyone who wishes to continue the work.

---

<details>
<summary>📜 <b>View Legacy README (Historical Project Information)</b></summary>

*The following is the original project documentation, preserved for historical context and for anyone who forks the repository.*

## Why ZedX AppImage?

The [Zed editor](https://zed.dev) is blazing fast, but lacks official AppImage releases. ZedX bridges that gap with:

- ✅ **Zero Installation** – Download once, run anywhere on any Linux distribution
- 🚀 **GPU Accelerated** – Full Vulkan support for 120 FPS rendering
- 📦 **Truly Portable** – All dependencies bundled (OpenSSL, XCB, XKB libraries included)
- 🔒 **Stable & Tested** – Built from official Zed source with quality assurance
- 💾 **Lightweight** – <150 MB compressed package with everything you need

## Downloads

**Choose the right build for your system:**

### 🏔️ Arch Build (Bleeding Edge)
- **File:** `zedX-v0.223.3-arch-x86_64.AppImage`
- **For:** Arch Linux, Fedora 40+, openSUSE Tumbleweed, and other rolling-release distros
- **Requirements:** glibc 2.38+ (check with `ldd --version`)
- **Optimized for:** Latest features and performance

### 🐧 Compatible Build (Stable Distros)
- **File:** `zedX-v0.223.3-compat-x86_64.AppImage`
- **For:** Debian 11-12, Ubuntu 20.04-24.04, RHEL 8-9, and enterprise Linux
- **Requirements:** glibc 2.31+ (most stable distros)
- **Recommended for:** Maximum compatibility

## Quick Start

```bash
# Download the compatible build (recommended)
wget https://github.com/debuggerdragon311/zedx-appimage/releases/latest/download/zedX-v0.223.4-compat+mix-x86_64.AppImage

# Make it executable
chmod +x zedX-v0.223.4-compat+mix-x86_64.AppImage

# Run immediately
./zedX-v0.223.4-compat+mix-x86_64.AppImage
```

## Portable Mode

Create `.home` and `.config` folders next to the AppImage to keep all settings portable:

```bash
# Create portable directories
mkdir zedX-v0.223.4-compat+mix-x86_64.AppImage.{home,config}

# Run - settings will be stored in these folders
./zedX-v0.223.4-compat+mix-x86_64.AppImage
```

## Building from Source

Want to build your own? Here's how:

### Prerequisites

```bash
# Install Rust toolchain
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# Clone Zed source
git clone https://github.com/zed-industries/zed.git
cd zed

# Build release binary
cargo build --release
```

### Create the AppImage

```bash
# Clone this repository
git clone https://github.com/debuggerdragon311/zedx-appimage.git
cd zedx-appimage

# Copy the Zed binary you just built
cp /path/to/zed/target/release/zed zed.fk.app/usr/bin/zed
chmod +x zed.fk.app/usr/bin/zed

# Download appimagetool
wget https://github.com/AppImage/AppImageKit/releases/download/continuous/appimagetool-x86_64.AppImage
chmod +x appimagetool-x86_64.AppImage

# Build the AppImage
./appimagetool-x86_64.AppImage zed.fk.app zedX-v0.223.4-compat+mix-x86_64.AppImage
```

## Credits

- **[Zed Industries](https://zed.dev)** – Original Zed editor developers
- **[AppImageKit](https://github.com/AppImage/AppImageKit)** – Portable packaging framework

## Important Disclaimer

⚠️ **This was an UNOFFICIAL community-maintained build.**

- **Not affiliated with:** Zed Industries, Inc.
- **Not endorsed by:** The official Zed development team
- **Official releases:** Available at [zed.dev](https://zed.dev)

</details>

<br>

<p align="center">
  <i>Made with ⚡ for the Linux community, forever.</i>
</p>
