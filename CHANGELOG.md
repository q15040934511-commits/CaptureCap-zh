# 更新日志

本文件只记录已由仓库文件、源码包或构建证据支持的变化。静态代码线索不会被写成真机测试通过。

## Unreleased

- 创建公开 GitHub Release，并上传 V0.3 Debug APK；明确其仅为测试构建，不是正式稳定发行包。
- 更正原版 `base.apk` 与 V0.3 Debug APK 的文件身份、签名和 SHA-256，详见 [APK_AUDIT.md](APK_AUDIT.md)。
- 核对 V0.3 构建源码 ZIP SHA-256：`e410f10fe59cb53105932d745d4945066c057eee69f1c279650c22c707ceaf03`。
- 核实 V0.3 `:app:assembleDebug` 成功，JVM 单元测试 41/41 通过。
- 如实记录 `:app:lintDebug` 失败：257 errors、1083 warnings、1 hint。
- 明确 Android 真机 A–F 功能测试全部 NOT RUN。
- 更正中文资源状态：存在部分简体中文本地化，但仍有未翻译资源。
- 在已核对 V0.3 源码中未找到可确认的 RAM-only 录制模式，不再将其列为已实现功能。
- 明确 V0.3 源码 ZIP 尚未上传至本 GitHub 仓库。

## V0.3 Debug 构建（非正式 Release）

- Application ID：`com.yepgoryo.CaptureCap`
- versionName：`3.9.8.8`
- versionCode：`46`
- APK SHA-256：`d24bfd3ec0e6f25ca59d50831319ec461e29315ade60628f6f2860918469e0f5`
- 详细信息见 [BUILD_REPORT.md](BUILD_REPORT.md)、[TEST_REPORT.md](TEST_REPORT.md) 和 [RELEASE_NOTES.md](RELEASE_NOTES.md)。
