# amneziawg-go-openwrt

AmneziaWG userspace implementation in Go for OpenWrt. Use this as a fallback when the kernel module is not available.

## What is AmneziaWG?

AmneziaWG is a contemporary version of the WireGuard protocol with protection against Deep Packet Inspection (DPI) systems.

## Why Userspace Implementation?

The Go implementation is useful when:
- Kernel module is not available for your device
- You need portability across different kernel versions
- Testing without loading kernel modules

## Performance Note

For production use, the **kernel module (kmod-amneziawg)** is recommended for better performance and lower resource usage.

## Installation

```bash
opkg update
opkg install amneziawg-go
```

## Building Requirements

This package requires Go 1.24.4 or later. Most OpenWrt stable releases include an older Go version.

### Updating Go in OpenWrt Build Tree

If building fails due to Go version, replace the golang package:

```bash
cd openwrt/feeds/packages/lang
rm -rf golang
# Clone latest golang package from OpenWrt packages
git clone https://github.com/openwrt/packages.git temp
cp -r temp/lang/golang .
rm -rf temp
```

## Verification

Check if binary is installed:

```bash
which amneziawg-go
/usr/bin/amneziawg-go --version
```

## How It Works

When both `kmod-amneziawg` and `amneziawg-go` are installed, the system prefers the kernel module. The Go implementation is used only as a fallback.

## License

MIT

## Links

- [amneziawg-tools-openwrt](https://github.com/xyzmean/amneziawg-tools-openwrt) - CLI tools
- [luci-proto-amneziawg](https://github.com/xyzmean/luci-proto-amneziawg) - Web UI
- [kmod-amneziawg-openwrt](https://github.com/xyzmean/kmod-amneziawg-openwrt) - Kernel module
