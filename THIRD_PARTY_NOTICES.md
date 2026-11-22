# 第三方组件与许可证说明

本文件基于当前 APK 中可见的许可证文件及资源目录做初步记录。**许可证文本存在，不足以独立确定每个文件、类或二进制组件的准确归属和版本。**

## APK 中发现的许可证文本

APK 中包含以下许可证文件：

| APK 路径 | 许可证文本 | 本仓库副本 |
|---|---|---|
| `assets/license.txt` | CaptureCap MIT notice（Copyright © 2026 Egor Olegovich Yakovlev） | `licenses/CaptureCap-APK-MIT.txt` |
| `META-INF/licenses/COPYING.GPL` | GNU GPL v2 | `licenses/COPYING.GPL` |
| `META-INF/licenses/COPYING.LGPL` | GNU LGPL v2.1 | `licenses/COPYING.LGPL` |
| `META-INF/licenses/COPYING.FDL` | GNU Free Documentation License 1.2 | `licenses/COPYING.FDL` |
| `META-INF/licenses/COPYING.Xiph` | Xiph.Org / Josh Coalson BSD 风格许可 | `licenses/COPYING.Xiph` |
| 多个 `META-INF/androidx/*/LICENSE.txt` | Apache License 2.0 | `licenses/Apache-2.0.txt` |

根目录 `LICENSE` 保留上游仓库当前发布的 MIT 许可证文本（Copyright (c) 2025 Egor Yakovlev）。APK 里嵌入的 MIT notice 年份为 2026，两份文本均保留以便溯源；正式发行时应确认各自适用范围和版权年份。

GPL/LGPL/FDL/Xiph 文本副本与 Xiph FLAC 1.4.3 源码发行包中的相同命名许可证文本一致。Apache 2.0 文本用于保留 APK 中 AndroidX 组件的许可证要求。

## 尚未确认的事项

仅凭 APK 中存在许可证文本，无法可靠判断每份许可证具体对应哪些二进制库、版本、代码路径、链接方式或修改内容。APK 还包含 `librtmp`、OpenSSL 相关 native library 和 `scrcpy-server` 资源。需要依据完整源码、依赖版本、构建配置和上游组件清单逐项确认实际组件与适用许可证。

## 发布前核查清单

1. 生成组件清单（SBOM），记录组件名称、版本、来源、许可证及 APK 对应路径。
2. 确认 GPL/LGPL 组件是否实际包含在发行物中，并满足适用义务，包括许可证副本、源码提供、修改标记及适用时的可重新链接材料。
3. 确认 Xiph 相关组件的版权声明、条件和免责声明得到保留。
4. 确认 OpenSSL、librtmp、scrcpy-server 和其他依赖的许可证及源代码获取义务。
5. 将准确的第三方源码、补丁或源码获取方式与对应 APK 版本绑定。
6. 不要把整个 APK 简化标注为“仅 MIT”。

这是基于当前 APK 文件的初步盘点，不是完整 SBOM，也不构成法律意见。
