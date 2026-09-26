# Bestechnic Binary Files

[简体中文](README.zh-CN.md)

`bestechnic-blobs` provides prebuilt BES2700YP platform support libraries for the Zephyr integration.

## Platform libraries

The three libraries are stored in `lib/bes2700yp/platform/`:

| File | Purpose |
|---|---|
| `libbes2700yp_system.a` | Clock, power, and other low-level system support |
| `libbes2700yp_flash.a` | Flash HAL, drivers, and device configuration |
| `libbes2700yp_bootstrap_compat.a` | Startup, CMSIS, and libc compatibility support |

[metadata.json](lib/bes2700yp/platform/metadata.json) records the library version, build profile, ABI, compiler, file sizes, SHA256 checksums, producer commit, and generated manifest checksum. The system library includes M55 PARK preparation for use while the peer CPU remains in reset.

## Fetching the libraries

In an initialized Zephyr workspace, fetch the libraries through the `hal_bestechnic` module:

```sh
west blobs fetch hal_bestechnic
```

The module pins a Git commit of this repository and verifies each downloaded file against its SHA256 checksum. Consumers of the module do not need to clone this repository separately. Use the repository revision specified by `hal_bestechnic` when integrating these libraries.

## Origin and use conditions

See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) for origin, third-party notices, and use conditions.
