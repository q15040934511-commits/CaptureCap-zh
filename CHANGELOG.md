# 更新日志

本文件区分构建自动化结果、维护者确认的实际测试和仍待归档的资料，不把缺失的测试数据写成已验证事实。

## Unreleased

- 更正公开 `v1.0.0` Release 的资产身份与功能描述，准备了可直接替换的 Release 正文，见 [RELEASE_CORRECTION.md](RELEASE_CORRECTION.md)。
- 明确 Release 中的 `CaptureCap-zh-v1.0.0.zip` 是 APK 的 ZIP 包装副本，不是 Android Studio 完整源码工程。
- 更新 V0.3 真机测试状态：项目维护者确认实际测试已完成，整体使用未发现重大问题。
- 更正此前“真机 A–F 全部 NOT RUN”的过时表述；构建主机当时未连接设备不代表项目后来没有完成真机测试。
- 明确当前仍缺少设备型号、Android 版本、逐项测试结果和原始记录，不虚构分项 PASS。
- 明确当前 V0.3 APK 可作为阶段版本提供体验和收集反馈，但仍为 Debug 签名构建，不是正式签名 Release variant。
- 保留原版 `base.apk` 与 V0.3 Debug APK 的文件身份、签名和 SHA-256 区分。
- 核对 V0.3 构建源码 ZIP SHA-256：`e410f10fe59cb53105932d745d4945066c057eee69f1c279650c22c707ceaf03`。
- 核实 V0.3 `:app:assembleDebug` 成功，JVM 单元测试 41/41 通过。
- 如实记录 `:app:lintDebug` 失败：257 errors、1083 warnings、1 hint。
- 更正中文资源状态：存在部分简体中文本地化，但仍有未翻译资源。
- 在已核对 V0.3 源码中未找到可确认的 RAM-only 录制模式，不将其列为已实现功能。
- 明确 V0.3 完整源码 ZIP 尚未上传至本 GitHub 仓库。

## V0.3 Debug 构建

- Application ID：`com.yepgoryo.CaptureCap`
- versionName：`3.9.8.8`
- versionCode：`46`
- APK SHA-256：`d24bfd3ec0e6f25ca59d50831319ec461e29315ade60628f6f2860918469e0f5`
- 详细信息见 [BUILD_REPORT.md](BUILD_REPORT.md)、[TEST_REPORT.md](TEST_REPORT.md) 和 [RELEASE_NOTES.md](RELEASE_NOTES.md)。
