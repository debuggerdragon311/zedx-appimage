<!-- >[!WARNING]
> **🚧 MAINTENANCE IN PROGRESS**  
> I'm improving compatibility across Linux distributions. New builds with better glibc support coming within 24-48 hours.  
> [Last stable release available here](https://github.com/debuggerdragon311/zedx-appimage/releases/tag/v0.223.4)
-->


# ZedX AppImage

[![Zed Version](https://img.shields.io/badge/Zed-v0.223.4-lightgreen.svg)](https://zed.dev)
[![License: AGPL-3.0](https://img.shields.io/badge/License-AGPL--3.0-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![GitHub release](https://img.shields.io/github/release/debuggerdragon311/zedx-appimage.svg)](https://github.com/debuggerdragon311/zedx-appimage/releases/v0.223.4)
[![Maintained](https://img.shields.io/badge/Maintained-Yes-green.svg)](https://github.com/debuggerdragon311/zedx-appimage)

> Portable, self-contained AppImage builds of the Zed high-performance code editor. Zero installation, maximum performance.

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

**Not sure which to download?** → Use the **compat** build (works everywhere)

[📥 Download Latest Release](https://github.com/debuggerdragon311/zedx-appimage/releases/latest)

## Quick Start

```bash
# Download the compatible build (recommended)
wget https://github.com/debuggerdragon311/zedx-appimage/releases/latest/download/zedX-v0.223.4-compat+mix-x86_64.AppImage

# Make it executable
chmod +x zedX-v0.223.4-compat+mix-x86_64.AppImage

# Run immediately
./zedX-v0.223.4-compat+mix-x86_64.AppImage
```

**That's it!** No package managers, no dependency hunting, no root required.

## Portable Mode

Create `.home` and `.config` folders next to the AppImage to keep all settings portable:

```bash
# Create portable directories
mkdir zedX-v0.223.4-compat+mix-x86_64.AppImage.{home,config}

# Run - settings will be stored in these folders
./zedX-v0.223.4-compat+mix-x86_64.AppImage
```

All configuration and data will be stored in these folders instead of `~/.config/`, making it truly portable across machines or USB drives.

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

# The binary will be at: target/release/zed
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

### Building for Maximum Compatibility

For the `-compat` build, we recommend building on Debian 12 or Ubuntu 22.04:

```bash
# On Debian 12 / Ubuntu 22.04
sudo apt update && sudo apt install -y \
    build-essential clang cmake curl git pkg-config \
    libx11-dev libx11-xcb-dev libxcb1-dev libxcb-render0-dev \
    libxcb-shape0-dev libxcb-xfixes0-dev libxkbcommon-dev \
    libxkbcommon-x11-dev libssl-dev libfontconfig1-dev \
    libfreetype6-dev libasound2-dev libvulkan-dev libwayland-dev \
    libxcursor-dev libxi-dev libxrandr-dev mesa-vulkan-drivers libzstd-dev

# Install Rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source "$HOME/.cargo/env"

# Build
export CC=clang
export CXX=clang++
cd zed
cargo build --release -j 2
```

## Troubleshooting

### Error: GLIBC version not found

You downloaded the `-arch` build but need the `-compat` build instead.

**Solution:** Download the `-compat` variant from releases.

**How to check your glibc version:**
```bash
ldd --version
```

If you see 2.36 or lower → use `-compat`  
If you see 2.38 or higher → either build works

### Permission Denied on External Drives

If you get `execv error: Permission denied`:

```bash
# Move to your home directory
mv zedX-*.AppImage ~/
cd ~
./zedX-*.AppImage
```

This happens when external drives are mounted with the `noexec` flag for security.

### Missing Vulkan Drivers

Ensure your GPU drivers are up to date:

```bash
# Check Vulkan support
vulkaninfo | grep "deviceName"

# Install Vulkan (if missing)
# Arch: sudo pacman -S vulkan-icd-loader
# Debian/Ubuntu: sudo apt install mesa-vulkan-drivers
# Fedora: sudo dnf install vulkan-loader
```

## Project Structure

```
zedx-appimage/
├── LICENSE                    # AGPL-3.0 license
├── README.md                  # This file
└── zed.fk.app/               # AppImage source directory
    ├── AppRun                # Launch script with portable mode support
    ├── zed.desktop           # Desktop integration
    ├── zed.png               # Application icon (512x512)
    └── usr/
        ├── bin/              # Binary location
        ├── lib/              # Bundled libraries (OpenSSL, XCB, etc.)
        └── share/            # Desktop files and icons
```

## What's Included

- **Zed Binary:** Built from official source (v0.225.0+dev)
- **Bundled Libraries:**
  - OpenSSL 3.x (`libssl.so.3`, `libcrypto.so.3`)
  - ALSA audio (`libasound.so.2`)
  - X11/Wayland support (`libxcb-xkb`, `libxkbcommon`)
  - C++ runtime (`libstdc++.so.6`)

## Roadmap

- [x] Multiple build variants for different distros
- [x] Portable configuration support
- [ ] Automated builds on new Zed releases
- [ ] Multiple architecture support (ARM64)
- [ ] Integration with AppImageHub
- [ ] Delta updates for faster releases

## Release Cadence

ZedX AppImage follows Zed's official releases with a slight delay for building and testing:

| Release Type | Description | Status |
|--------------|-------------|--------|
| 🔥 **Development** | Latest `main` branch features | Usually available within 24h |
| 🧪 **Pre-release** | Beta versions for testing | Available on request |
| ✅ **Stable** | Production-ready releases | Priority, typically within 48h |

**Current Status:**
- Latest Dev: ✅ v0.225.0+dev (multiple variants)
- Stable: ✅ v0.223.3

## FAQ

### Which AppImage should I download?

**Short answer:** Download the `-compat` build unless you're on Arch/Fedora.

**Long answer:**
- `-arch`: Built on latest systems, optimized for bleeding-edge distros (glibc 2.38+)
- `-compat`: Built on Debian 12, works on stable and older systems (glibc 2.31+)

### Can I run multiple instances?

Yes! Use the `--new-window` flag:

```bash
./zedX-*.AppImage --new-window
```

### How do I update?

Simply download the new AppImage and replace the old one. Your settings in `~/.config/zed/` are preserved (or in portable `.config/` folder if using portable mode).

## Contributing

Contributions welcome! Feel free to:
- Report bugs via [Issues](https://github.com/debuggerdragon311/zedx-appimage/issues)
- Submit improvements via [Pull Requests](https://github.com/debuggerdragon311/zedx-appimage/pulls)
- Request features or suggest optimizations

## Credits

- **[Zed Industries](https://zed.dev)** – Original Zed editor developers
- **[AppImageKit](https://github.com/AppImage/AppImageKit)** – Portable packaging framework
- **Community** – Testing and feedback

## License

This repository is licensed under **AGPL-3.0** to match Zed's licensing requirements.

- **Zed Editor:** [AGPL-3.0](https://github.com/zed-industries/zed/blob/main/LICENSE-AGPL) or [GPL-3.0](https://github.com/zed-industries/zed/blob/main/LICENSE-GPL)
- **Build Scripts & Packaging:** AGPL-3.0 (this repository)

## Important Disclaimer

⚠️ **This is an UNOFFICIAL community-maintained build.**

- **Not affiliated with:** Zed Industries, Inc.
- **Not endorsed by:** The official Zed development team
- **Official releases:** Available at [zed.dev](https://zed.dev)
- **Support:** For Zed-specific issues, please visit the [official repository](https://github.com/zed-industries/zed)

**Quality Commitment:** While this is an unofficial build, I am committed to:
- ✓ Building from official, unmodified Zed source code
- ✓ Regular updates following upstream releases
- ✓ Transparency in build process and dependencies
- ✓ Prompt bug fixes and community support

For official support, enterprise features, or commercial use, please visit [zed.dev](https://zed.dev).

---

<p align="center">
  Made with ⚡ for the Linux community
</p>
