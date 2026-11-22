# CaptureCap-zh

**CaptureCap 的非官方中文增强版本。** 本仓库用于维护汉化、功能改动、构建来源、版本发布与第三方许可证信息。

> 本项目不是 CaptureCap 官方发行版。上游项目：[yepgoryo/CaptureCap](https://github.com/yepgoryo/CaptureCap)，上游作者：**Egor Yakovlev**。本改版署名：**Di dh D'HDrd**。请勿混淆本项目与上游官方版本。

## 当前状态

仓库文档正在完善，当前交付的 APK 已完成静态核验，报告见 [APK_AUDIT.md](APK_AUDIT.md)。

**当前 APK 是 Debug 构建，不适合直接作为正式公开 Release。** 它带有 Android Debug 测试证书，并在 Manifest 中声明 `debuggable=true`。请在生成正式发布包前重新构建 Release variant、签名并完成设备测试。

APK 中可见 WAV/FLAC 无损 PCM 音频处理及中断 session 恢复相关代码；但 RAM 临时存储是否为完整可选功能仍需源码和设备验证。该 APK 的资源字符串中没有找到可确认的简体中文本地化文本，因此暂不能称为完整中文汉化发行版。

## 改版方向

- 中文本地化；
- RAM 临时存储（实现方式及边界仍待源码核验）；
- WAV/FLAC 无损 PCM 音频录制与恢复保护（静态代码线索已发现，设备测试待完成）。

“无损”是指 WAV/FLAC 对输入 PCM 音频的编码方式，不代表能恢复录制源头已经丢失的音质。

## 下载

正式 APK 应通过 [GitHub Releases](https://github.com/q15040934511-commits/CaptureCap-zh/releases) 发布。当前 Debug APK 不作为正式公开下载版本。每个 Release 应附版本号、完整变更说明、SHA-256、签名信息，以及与 APK 对应的源码提交或源码压缩包。

## 文档

- [APK 静态核验报告](APK_AUDIT.md)
- [上游来源与基线](UPSTREAM.md)
- [更新日志](CHANGELOG.md)
- [第三方组件与许可证说明](THIRD_PARTY_NOTICES.md)
- [隐私与数据处理说明](PRIVACY.md)
- [首个 APK 发布核验记录](RELEASE_NOTES.md)

## 许可证

根目录 `LICENSE` 对应 CaptureCap 上游项目当前公布的 MIT 许可证。APK 内嵌的 MIT 文本副本另存于 `licenses/CaptureCap-APK-MIT.txt`。APK 同时包含 GPL、LGPL、FDL、Xiph 和 AndroidX Apache 2.0 等许可证文本；请阅读 [第三方许可证说明](THIRD_PARTY_NOTICES.md)。不能把 APK 整体简化描述为“仅 MIT”。

## 源码状态

目前仓库尚未提交完整修改后的 Android Studio 工程，因此不是可复现构建的完整源码仓库。正式发布前需要补入完整源码、依赖锁定/版本信息、构建说明和可对应到 APK 的提交记录。

## 隐私

APK 声明了录音、摄像头、网络、悬浮窗、通知及 Shizuku 相关权限。权限声明不等于实际行为，但网络行为和数据流尚未完成审计。详情见 [PRIVACY.md](PRIVACY.md)。

## 反馈

欢迎通过 GitHub Issues 提交可复现的问题。请注明 APK 版本、Android 版本、设备型号、复现步骤和实际结果；上传日志前请移除个人信息。
