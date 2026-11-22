# 第三方组件与许可证说明

本文件是初步清单，不是完整 SBOM 或法律意见。必须区分“APK 中存在许可证文本”和“已经确认该文本对应某个具体二进制组件”；二者不能直接画等号。

## 已观察到的 APK 许可证文本

| APK 路径 | 文本 | 当前处理 |
|---|---|---|
| `assets/license.txt` | CaptureCap MIT notice，Copyright © 2026 Egor Olegovich Yakovlev | 保留于 `licenses/CaptureCap-APK-MIT.txt` |
| `META-INF/licenses/COPYING.GPL` | GNU GPL v2 | 已保留文本；对应组件仍待映射 |
| `META-INF/licenses/COPYING.LGPL` | GNU LGPL v2.1 | 已保留文本；对应组件仍待映射 |
| `META-INF/licenses/COPYING.FDL` | GNU FDL 1.2 | 已保留文本；对应组件仍待映射 |
| `META-INF/licenses/COPYING.Xiph` | Xiph.Org / Josh Coalson BSD 风格许可 | 已保留文本 |
| `META-INF/androidx/*/LICENSE.txt` | Apache License 2.0 | 已保留标准文本 |

根目录 `LICENSE` 是上游 CaptureCap 仓库的 MIT 文本（Copyright (c) 2025 Egor Yakovlev）；APK 内嵌 MIT notice 使用 2026 年份。两份文本均保留，适用范围和版权年份仍应结合上游历史及实际代码核对。

## 从 V0.3 构建源码确认的依赖

### libflac-java 1.4.3.1

源码工程在 `app/libs/libflac-java-1.4.3.1.jar` 使用该库。Maven Central 元数据列出：
- FLAC codec / metadata：BSD 3-Clause；
- ReplayGain analysis / synthesis：GNU LGPL 2.1 or later。

来源：[Maven Central - io.github.raphimc:libflac-java:1.4.3.1](https://central.sonatype.com/artifact/io.github.raphimc/libflac-java)。

需要继续核实 APK 实际调用的类是否涉及 ReplayGain 模块，并补齐适用的 BSD 3-Clause 文本及 LGPL 对应源码/重新链接材料（如适用）。不要因为 APK 中已有一份 LGPL 文本就认为义务已全部满足。

### scrcpy-server 4.1

V0.3 的 `app/build.gradle.kts` 固定下载 Genymobile scrcpy-server 4.1，并校验 SHA-256：
`deacb991ed2509715160ffdc7907e47b4160eb30d1566217e9047fd5b8850cae`。

scrcpy v4.1 上游仓库的 LICENSE 为 Apache License 2.0：
- 源码：[Genymobile/scrcpy v4.1](https://github.com/Genymobile/scrcpy/tree/v4.1)
- 许可证：[v4.1/LICENSE](https://github.com/Genymobile/scrcpy/blob/v4.1/LICENSE)

因此，不应把 APK 中的 GPL v2 文本直接认定为 scrcpy-server 的许可证。应保留 Apache 2.0 归属，并在最终发行物中确认 NOTICE/许可证材料位置。

## 仍需逐项确认的二进制组件

APK 中还观察到 `librtmp`、OpenSSL 相关 native libraries，以及 scrcpy-server 等资源。应结合完整依赖树、打包路径、二进制指纹和上游版本逐项确认它们的来源与许可证。当前不能对这些组件作出完整许可结论。

## 发布前清单

1. 生成并提交 SBOM，至少包含组件名、准确版本、来源、许可证、APK 路径和哈希。
2. 为每个打包组件建立二进制到依赖/源码的映射。
3. 确认 GPL/LGPL 组件是否实际包含在发行物中，并满足适用的源码提供、修改标记和重新链接义务。
4. 补齐 BSD 3-Clause 文本；核对 Xiph 版权声明、条件和免责声明。
5. 保留 scrcpy 4.1 Apache 2.0 许可证及相应归属。
6. 确认 OpenSSL、librtmp、AndroidX 及其他依赖的准确版本与许可证。
7. 将匹配 APK 的源码、补丁和构建说明绑定到同一 Release tag。

在上述事项完成前，不要将整个 APK 简化标注为“仅 MIT”。
