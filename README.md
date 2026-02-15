# ZedX AppImage

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub release](https://img.shields.io/github/release/yourusername/zedx-appimage.svg)](https://github.com/yourusername/zedx-appimage/releases)

Portable AppImage builds of the [Zed](https://zed.dev) high-performance code editor. Run Zed anywhere on Linux without installation.

## Features

- ✅ **Zero Installation** - Download and run immediately
- 🔒 **Optional Encryption** - AES-256 encrypted variant with password protection
- 💾 **Portable Config** - Settings stored in `~/.config/zedx-portable/`
- 🚀 **GPU Accelerated** - Full performance with Vulkan support
- 📦 **Self-Contained** - All dependencies bundled

## Downloads

### Standard Build
```bash
wget https://github.com/yourusername/zedx-appimage/releases/latest/download/zedX-v0.225.0-x86_64.AppImage
chmod +x zedX-v0.225.0-x86_64.AppImage
./zedX-v0.225.0-x86_64.AppImage
```

### Encrypted Build (Password Protected)
```bash
wget https://github.com/yourusername/zedx-appimage/releases/latest/download/zedX-encrypted-v0.225.0-x86_64.AppImage
chmod +x zedX-encrypted-v0.225.0-x86_64.AppImage
./zedX-encrypted-v0.225.0-x86_64.AppImage
# Enter password when prompted
```

## Build from Source

### Prerequisites
```bash
# Install dependencies
sudo pacman -S base-devel rust cargo  # Arch
sudo apt install build-essential rustc cargo  # Debian/Ubuntu

# Install appimagetool
wget https://github.com/AppImage/AppImageKit/releases/download/continuous/appimagetool-x86_64.AppImage
chmod +x appimagetool-x86_64.AppImage
```

### Standard Build
```bash
git clone https://github.com/yourusername/zedx-appimage.git
cd zedx-appimage
./build-standard.sh
```

### Encrypted Build
```bash
./build-encrypted.sh
# Set your encryption password when prompted
```

## Configuration

Settings are stored in:
- **Linux:** `~/.config/zedx-portable/`

This ensures your configuration persists between sessions while keeping the AppImage portable.

## Encryption Details

The encrypted variant uses:
- **Algorithm:** AES-256-CBC
- **Key Derivation:** PBKDF2
- **Runtime:** Binary decrypted to `/dev/shm` (RAM)
- **Cleanup:** Automatic removal after exit

**Security Note:** The decrypted binary exists in RAM only while running. Never written to disk.

## Troubleshooting

### Permission Denied Error
If you get `execv error: Permission denied`:
```bash
# Option 1: Move to home directory
mv zedX-*.AppImage ~/
cd ~
./zedX-*.AppImage

# Option 2: Extract and run
./zedX-*.AppImage --appimage-extract
./squashfs-root/AppRun
```

This usually happens on external drives mounted with `noexec`.

### Missing Dependencies
The AppImage bundles all required libraries. If you encounter issues, ensure your system has:
- OpenSSL 3.x (for encrypted builds)
- Vulkan drivers (for GPU acceleration)

## Credits

- [Zed Editor](https://zed.dev) - Original software by Zed Industries
- Built with [AppImageKit](https://github.com/AppImage/AppImageKit)

## License

This repository contains build scripts and packaging. Zed editor is licensed under GPL-3.0. See [Zed's license](https://github.com/zed-industries/zed/blob/main/LICENSE-GPL) for details.

Build scripts: MIT License

## Disclaimer

This is an unofficial build. For official releases, visit [zed.dev](https://zed.dev).
```
