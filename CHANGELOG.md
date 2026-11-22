# 更新日志

本文件只记录已经核实的仓库或 APK 变化。静态代码线索不会被写成已通过设备测试的功能。

## Unreleased

- 完善项目首页、上游来源、APK 核验和第三方许可证文档。
- 静态检查当前 APK：识别 WAV/FLAC PCM 无损音频处理及 lossless session 恢复相关代码。
- 发现当前 APK 是 Debug 构建（`debuggable=true`，Android Debug 测试证书），暂不适合正式发布。
- 中文资源和 RAM 临时存储行为仍待完整源码与设备核验。
- 完整修改后 Android Studio 源码尚未入库。

## 当前 APK（静态核验，不是正式 Release）

- versionName：3.9.8.8
- versionCode：46
- 详细信息见 [APK_AUDIT.md](APK_AUDIT.md)。
