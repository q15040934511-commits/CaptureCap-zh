# CaptureCap-zh

**CaptureCap 的非官方中文增强版本。** 本仓库用于维护上游来源、中文本地化、WAV/FLAC 高保真音频改动、构建记录和第三方许可证信息。

> 本项目不是 CaptureCap 官方发行版。上游项目：[yepgoryo/CaptureCap](https://github.com/yepgoryo/CaptureCap)，上游作者：**Egor Yakovlev**。本改版署名：**Di dh D'HDrd**。请勿混淆本项目与上游官方版本。

## 当前状态

**目前没有可供普通用户下载的正式 Release。** 当前 V0.3 APK 是 Debug 构建，不应作为正式公开发行包。

仓库此前把原版 `base.apk` 与 V0.3 Debug APK 混为一谈，现已在审计文档中更正：
- 原版 `base.apk`：29,852,405 bytes，原作者签名，无本项目新增 Hi-Fi 类。
- V0.3 Debug APK：30,597,172 bytes，Android Debug 签名，arm64-v8a only，`debuggable=true`。

V0.3 对应的完整源码包和构建证据已在项目工作材料中核对 SHA-256，但**源码 ZIP 尚未上传到本 GitHub 仓库**。当前仓库因此仍不是可直接下载源码并复现构建的完整仓库。详情见 [SOURCE_ARCHIVE.md](SOURCE_ARCHIVE.md)。

## 已核实的 V0.3 内容

- 源码中存在 WAV/FLAC PCM16 录音实现和中断 Session 恢复逻辑。
- `:app:assembleDebug` 构建成功。
- JVM 单元测试 41/41 通过。
- `:app:lintDebug` 失败：257 errors、1083 warnings、1 hint。
- 所有 Android 真机 A–F 运行测试均为 **NOT RUN**，不能据此宣称真机录音稳定。
- 简体中文资源是**部分本地化**，不是完整汉化。匹配构建源码的默认资源有 314 个 string 项，`values-zh-rCN` 有 181 个，仍有 133 个 string key 缺失。
- 在已核对的 V0.3 源码中，没有找到可确认的“全部录制数据仅存 RAM”模式实现，因此目前不把 RAM 临时存储列为已实现功能。

详细证据：
- [APK 身份与静态核验](APK_AUDIT.md)
- [构建报告](BUILD_REPORT.md)
- [功能测试报告](TEST_REPORT.md)
- [源码包指纹与选择说明](SOURCE_ARCHIVE.md)
- [第三方组件与许可证说明](THIRD_PARTY_NOTICES.md)

## 改版方向

- 完善简体中文本地化；
- WAV/FLAC PCM16 高保真音频录制；
- 录制 Session 日志、异常中断标记与恢复保护；
- 保留原版 AAC/M4A 路径和原有界面结构。

“无损”是指 WAV/FLAC 对输入 PCM 音频的编码方式，不代表能恢复录制源头已经丢失的音质。

## 下载

正式 APK 应通过 [GitHub Releases](https://github.com/q15040934511-commits/CaptureCap-zh/releases) 发布。当前 Debug APK 不作为正式公开下载版本。正式 Release 应附版本号、完整变更说明、SHA-256、签名信息，以及与 APK 对应的源码提交或源码包。

## 许可证

根目录 `LICENSE` 保留 CaptureCap 上游仓库公布的 MIT 许可证文本。APK 内另有不同年份的 MIT notice，以及 Apache、BSD、LGPL、GPL、FDL、Xiph 等许可证文本。不能把整个 APK 简化描述为“仅 MIT”。具体组件映射仍有未解决项，见 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)。

## 隐私

权限声明不等于实际数据行为。本项目尚未完成完整网络行为与数据流审计，不能承诺应用完全离线或不会上传数据。详情见 [PRIVACY.md](PRIVACY.md)。

## 反馈

欢迎通过 GitHub Issues 提交可复现的问题。请注明 APK 版本、Android 版本、设备型号、复现步骤和实际结果；上传日志前请移除个人信息。
