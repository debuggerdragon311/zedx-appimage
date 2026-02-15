# ZedX AppImage

[![Zed Version](https://img.shields.io/badge/Zed-v0.225.0-lightgreen.svg)](https://zed.dev)
[![License: AGPL-3.0](https://img.shields.io/badge/License-AGPL--3.0-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![GitHub release](https://img.shields.io/github/release/debuggerdragon311/zedx-appimage.svg)](https://github.com/debuggerdragon311/zedx-appimage/releases)
[![Maintained](https://img.shields.io/badge/Maintained-Yes-green.svg)](https://github.com/debuggerdragon311/zedx-appimage)

> Portable, self-contained AppImage builds of the Zed high-performance code editor. Zero installation, maximum performance.

## Why ZedX AppImage?

The [Zed editor](https://zed.dev) is blazing fast, but lacks official AppImage releases. ZedX bridges that gap with:

- ✅ **Zero Installation** – Download once, run anywhere on any Linux distribution
- 🚀 **GPU Accelerated** – Full Vulkan support for 120 FPS rendering
- 📦 **Truly Portable** – All dependencies bundled (OpenSSL, XCB, XKB libraries included)
- 🔒 **Stable & Tested** – Built from official Zed source with quality assurance
- 💾 **Lightweight** – <250 MB compressed package with everything you need

## Quick Start

```bash
# Download the latest release
wget https://github.com/debuggerdragon311/zedx-appimage/releases/latest/download/zedX-dev-v0.225.0-arch-x86_64.AppImage

# Make it executable
chmod +x zedX-dev-v0.225.0-arch-x86_64.AppImage

# Run immediately
./zedX-dev-v0.225.0-arch-x86_64.AppImage
```

**That's it!** No package managers, no dependency hunting, no root required.

## System Requirements

- **OS:** Any modern Linux distribution (kernel 4.x+)
- **Graphics:** Vulkan-capable GPU with updated drivers
- **Architecture:** x86_64 (64-bit)
- **Disk Space:** 610 MB

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
./appimagetool-x86_64.AppImage zed.fk.app zedX-dev-v0.225.0-arch-x86_64.AppImage
```

## Troubleshooting

### Permission Denied on External Drives

If you get `execv error: Permission denied`:

```bash
# Move to your home directory
mv zedX-dev-v0.225.0-arch-x86_64.AppImage ~/
cd ~
./zedX-dev-v0.225.0-arch-x86_64.AppImage
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
```

## Project Structure

```
zedx-appimage/
├── LICENSE                    # AGPL-3.0 license
├── README.md                  # This file
└── zed.fk.app/               # AppImage source directory
    ├── AppRun                # Launch script
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

- [ ] Automated builds on new Zed releases
- [ ] Multiple architecture support (ARM64)
- [ ] Minimal variant without bundled libs
- [ ] Integration with AppImageHub

## Release Cadence

ZedX AppImage follows Zed's official releases with a slight delay for building and testing:

| Release Type | Description | Status |
|--------------|-------------|--------|
| 🔥 **Development** | Latest `main` branch features | Usually available within 24h |
| 🧪 **Pre-release** | Beta versions for testing | Available on request |
| ✅ **Stable** | Production-ready releases | Priority, typically within 48h |

**Current Status:**
- Latest Dev: ✅ v0.225.0+dev
- Pre-release: ⏳ v0.224.1-pre (coming soon)
- Stable: ✅ v0.223.3

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
