# Bestechnic 二进制文件

[English](README.md)

`bestechnic-blobs` 提供 BES2700YP 的预编译平台支持库，供 Zephyr 集成使用。

## 平台支持库

候选版本 **0.2.0-rc1** 的三个库位于 `lib/bes2700yp/platform/`：

| 文件 | 内容 |
|---|---|
| `libbes2700yp_system.a` | 时钟、电源及其他底层系统支持 |
| `libbes2700yp_flash.a` | Flash HAL、驱动及型号配置 |
| `libbes2700yp_bootstrap_compat.a` | 启动、CMSIS 和 libc 兼容支持 |

[metadata.json](lib/bes2700yp/platform/metadata.json) 记录适用配置、工具链、文件大小和 SHA256。库使用 `dual_v1_24m_t2` 配置、`cortex-m33-fpv5-sp-d16-hard` ABI 和 GNU Arm Embedded 10.3-2021.10 工具链构建。
system 库增加 M55 CPU 保持复位时的 PARK 准备接口；flash 与 bootstrap_compat 库和 0.1.0 版本逐字节一致。元数据记录生成源码提交和生成 manifest 校验值；本候选尚待实板验证。

## 获取与版本

Zephyr 开发者通过 `hal_bestechnic` 模块的 `zephyr/module.yml` 获取配套库，在已初始化的工作区执行：

```sh
west blobs fetch hal_bestechnic
```

`hal_bestechnic` 模块固定所需的 Git 提交，并校验下载文件的 SHA256。使用该模块时无需单独克隆本仓。

库版本以本仓 Git 提交区分；集成时应使用 `hal_bestechnic` 指定的版本。

## 来源与使用条件

文件来源、第三方声明及使用条件见 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)。
