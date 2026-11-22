# CaptureCap-zh

**CaptureCap 的非官方中文增强版本。** 本仓库用于维护上游来源、中文本地化、WAV/FLAC 高保真音频改动、构建记录和第三方许可证信息。

> 本项目不是 CaptureCap 官方发行版。上游项目：[yepgoryo/CaptureCap](https://github.com/yepgoryo/CaptureCap)，上游作者：**Egor Yakovlev**。本改版署名：**Di dh D'HDrd**。请勿混淆本项目与上游官方版本。

## 当前状态

**V0.3 已完成维护者反馈的真机实际测试，整体使用未发现重大问题；当前 APK 已具备对外提供体验和收集反馈的条件。** 本项目仍将它明确标记为 V0.3 Debug 构建，而不是已完成正式签名和全部发布审查的 Production Release。

当前公开的 GitHub Release 使用 tag `v1.0.0`，Release 标题为 `CaptureCap-zh-v1.0.0.apk`。其中 APK 资产名称为 `base.apk`，已核验信息如下：

- 文件大小：30,597,172 bytes
- SHA-256：`d24bfd3ec0e6f25ca59d50831319ec461e29315ade60628f6f2860918469e0f5`
- 包名：`com.yepgoryo.CaptureCap`
- APK 内部 versionName / versionCode：`3.9.8.8 / 46`
- ABI：仅 arm64-v8a
- 签名：Android Debug；Manifest 为 `debuggable=true`

**版本号说明：** GitHub Release tag `v1.0.0` 是仓库发布标签，不会改变 APK 内部的 `3.9.8.8 / 46`。当前二进制仍属于 V0.3 Debug 构建。

**Release 描述更正：** 公开 Release 的旧描述曾列出 RAM 临时存储和中文界面本地化。根据当前源码审计，RAM-only 模式未能证实，简体中文也只是部分本地化。请参阅 [Release 页面更正说明](RELEASE_CORRECTION.md)，不要将这两项误认为已完整实现。

**ZIP 资产说明：** Release 中名为 `CaptureCap-zh-v1.0.0.zip` 的文件只是 APK 的 ZIP 包装副本，不是 Android Studio 完整源码工程。真正的 V0.3 完整源码包及其 SHA-256 见 [源码包说明](SOURCE_ARCHIVE.md)；该二进制源码 ZIP 目前仍待上传至仓库的 `source/` 目录。

真机测试状态已根据项目维护者最新确认更新。当前尚未提供可归档的设备型号、Android 版本、逐项测试矩阵和测试日志，因此文档不会将每一项测试伪写成独立的 PASS 记录。详细说明见 [TEST_REPORT.md](TEST_REPORT.md)。

**安装兼容性提醒：** 该 APK 使用 Debug 签名，与原作者签名版不同，不能直接覆盖安装原作者版本。安装前请备份重要数据；不要为了安装测试包而贸然卸载已有应用。

GitHub Releases 自动生成的 Source code ZIP/tar.gz 只是仓库提交快照，不等同于此 Android Studio 完整工程源码包。

## 已核实的 V0.3 内容

- 源码中存在 WAV/FLAC PCM16 录音实现和中断 Session 恢复逻辑。
- `:app:assembleDebug` 构建成功。
- JVM 单元测试 41/41 通过。
- 维护者已确认完成真机实际测试，整体无重大问题；分项设备、系统版本和原始记录尚未归档。
- `:app:lintDebug` 失败：257 errors、1083 warnings、1 hint。该结果已如实保留，不能称为 Lint 全部通过。
- 简体中文资源是**部分本地化**：匹配构建源码的默认资源有 314 个 string 项，`values-zh-rCN` 有 181 个，仍有 133 个 string key 缺失。
- 在已核对的 V0.3 源码中，没有找到可确认的“全部录制数据仅存 RAM”模式实现，因此目前不把 RAM 临时存储列为已实现功能。

详细证据：
- [APK 身份与静态核验](APK_AUDIT.md)
- [构建报告](BUILD_REPORT.md)
- [功能测试报告](TEST_REPORT.md)
- [源码包指纹与选择说明](SOURCE_ARCHIVE.md)
- [第三方组件与许可证说明](THIRD_PARTY_NOTICES.md)
- [发布前检查清单](RELEASE_CHECKLIST.md)

## 改版方向

- 完善简体中文本地化；
- WAV/FLAC PCM16 高保真音频录制；
- 录制 Session 日志、异常中断标记与恢复保护；
- 保留原版 AAC/M4A 路径和原有界面结构。

“无损”是指 WAV/FLAC 对输入 PCM 音频的编码方式，不代表能恢复录制源头已经丢失的音质。

## 下载

[查看 GitHub Releases](https://github.com/q15040934511-commits/CaptureCap-zh/releases)

当前 V0.3 APK 可以作为已完成维护者真机体验测试的阶段版本对外提供；请同时展示 APK 哈希、Debug 签名、arm64-v8a 限制和真机测试记录边界。若后续发布正式稳定版，仍应构建 Release variant、使用妥善保管的正式签名密钥、完成剩余 Lint 与许可证核查，并上传与 APK 精确对应的源码包。

## 许可证

根目录 `LICENSE` 保留 CaptureCap 上游仓库公布的 MIT 许可证文本。APK 内另有不同年份的 MIT notice，以及 Apache、BSD、LGPL、GPL、FDL、Xiph 等许可证文本。不能把整个 APK 简化描述为“仅 MIT”。具体组件映射仍有未解决项，见 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)。

## 隐私

权限声明不等于实际数据行为。本项目尚未完成完整网络行为与数据流审计，不能承诺应用完全离线或不会上传数据。详情见 [PRIVACY.md](PRIVACY.md)。

## 反馈

欢迎通过 GitHub Issues 提交可复现的问题。请注明 APK 版本、Android 版本、设备型号、复现步骤和实际结果；上传日志前请移除个人信息。不要在公开 Issue、提交记录或聊天截图中发布签名密钥、密码、访问令牌或个人录音。
