# Bestechnic 二进制文件

[English](README.md)

`bestechnic-blobs` 提供 BES2700YP 的预编译平台支持库，供 Zephyr 集成使用。

## 平台支持库

三个静态库位于 `lib/bes2700yp/platform/`：

| 文件 | 内容 |
|---|---|
| `libbes2700yp_system.a` | 时钟、电源及其他底层系统支持 |
| `libbes2700yp_flash.a` | Flash HAL、驱动及型号配置 |
| `libbes2700yp_bootstrap_compat.a` | 启动、CMSIS 和 libc 兼容支持 |

[metadata.json](lib/bes2700yp/platform/metadata.json) 记录库版本、构建配置、ABI、工具链、文件大小、SHA256、生成仓提交及生成 manifest 的校验值。system 库包含 M55 CPU 保持复位时使用的 PARK 准备接口。

## 获取与集成

Zephyr 开发者通过 `hal_bestechnic` 模块的 `zephyr/module.yml` 获取配套库，在已初始化的工作区执行：

```sh
west blobs fetch hal_bestechnic
```

`hal_bestechnic` 模块固定所需的 Git 提交，并校验下载文件的 SHA256。使用该模块时无需单独克隆本仓。

集成时应使用 `hal_bestechnic` 固定的本仓提交及文件哈希。

## 来源与使用条件

文件来源、第三方声明及使用条件见 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)。
