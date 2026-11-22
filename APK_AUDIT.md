# APK 静态核验报告

核验对象：当前交付的 `base.apk`。本报告仅记录可从 APK 二进制静态检查及已核对的上游仓库中确认的事实，不代表在真实设备上完成了运行测试。

## 文件身份

- 原文件名：`base.apk`
- 文件大小：30,597,172 bytes
- SHA-256：`d24bfd3ec0e6f25ca59d50831319ec461e29315ade60628f6f2860918469e0f5`
- Application ID：`com.yepgoryo.CaptureCap`
- versionName：`3.9.8.8`
- versionCode：`46`
- minSdkVersion：`24`
- targetSdkVersion：`37`
- compileSdkVersion：`37`
- Android Gradle Plugin 元数据：`9.4.1`

## 关键发布风险

**这份 APK 是 Debug 构建，不应直接作为公开正式版 Release 发布。**

核验到的证据：

- AndroidManifest 中 `android:debuggable=true`。
- DEX 构建元数据标记 `compilation-mode=debug`。
- APK v2 签名证书为自签名 Android Debug 证书：`CN=Android Debug, O=Android, C=US`。
- 证书序列号：`01`。
- 证书有效期：2026-10-18 至 2056-10-10。
- 证书 SHA-256 指纹：`5D:79:52:2A:8F:61:B8:4F:8D:77:51:21:A1:2E:DB:D6:DA:49:CB:9D:46:F2:D8:DD:31:F1:E2:7E:25:FC:C6:3E`。

正式发布前应从完整修改后源码构建 Release variant，使用项目所有者自行管理的发布密钥签名，确认 Manifest 不可调试，并在目标 Android 设备上回归测试。不要将调试签名密钥或私钥提交到仓库。

## APK 中观察到的功能线索

静态资源与 DEX 中存在以下标识：

- 音频文件格式选项包含 WAV 与 FLAC。
- 提示文本明确说明 WAV/FLAC lossless 模式要求本地纯音频录制，并限制麦克风、通话音频和直播等组合。
- DEX 中包含 `FlacPcm16Writer`、`FlacPcm16Decoder`、`WavPcm16Writer`、`PcmCapturePipeline`、`HighFidelityAudioCapture`、`LosslessSessionJournal` 等类名。
- `ScreenRecorder` 中可见 lossless session、临时文件、空间监控和启动时恢复中断 session 等符号。

这些证据支持“APK 中包含 WAV/FLAC 无损 PCM 音频处理路径及 session 恢复相关代码”的判断，但**不等于已经完成运行测试**，也不能仅凭类名证明所有边界情况均正常。

### RAM 临时存储

APK 中存在 PCM 队列、音频缓冲及 lossless 临时 session 管理相关符号，但目前无法仅凭这些符号确认是否存在用户可选择的“全部录制数据仅存 RAM”模式，也无法确认它的内存上限、落盘时机和异常退出行为。该功能状态标记为**待源码与设备测试核实**。

### 中文本地化

对 APK 的资源字符串进行检查，没有找到可确认的简体中文资源文本。当前不能把这份 APK 标记为“完整中文汉化版”。需要检查并补齐实际的中文资源，再重新构建验证。

## Manifest 声明的权限

本 APK 声明了以下权限（列出的是 Manifest 声明，不代表每项权限在每次使用时都会被调用）：

- `RECORD_AUDIO`
- `MODIFY_AUDIO_SETTINGS`
- `FOREGROUND_SERVICE`
- `FOREGROUND_SERVICE_MEDIA_PROJECTION`
- `FOREGROUND_SERVICE_MICROPHONE`
- `FOREGROUND_SERVICE_CAMERA`
- `SYSTEM_ALERT_WINDOW`
- `READ_EXTERNAL_STORAGE`
- `WRITE_EXTERNAL_STORAGE`（maxSdkVersion 28）
- `POST_NOTIFICATIONS`
- `START_ACTIVITIES_FROM_BACKGROUND`
- `INTERNET`
- `CAMERA`
- `ACCESS_NETWORK_STATE`
- `WAKE_LOCK`
- `moe.shizuku.manager.permission.API_V23`

由于存在网络权限，不能仅凭此 APK 断言应用完全离线。需要进一步对网络目标、数据流和隐私行为进行审计。

## 上游基线对照

已检查上游仓库 `yepgoryo/CaptureCap` 的 main 分支提交：

- 上游提交：`c647f9fdb4409a950e913e50ed0d22b7944165db`
- 提交日期：2026-11-09
- 提交说明：`Fix crashing when requesting permissions`

上游 `app/build.gradle.kts` 当前的 package、versionName、versionCode、minSdk、targetSdk 和 compileSdk 与 APK Manifest 中的对应值一致。这说明 APK 的版本元数据与该上游源码快照相符，但**不能单凭这些字段证明 APK 完全由该提交构建**。

APK 中另有 lossless 音频类与自定义 session 管理符号；需要以用户实际修改后的源码和提交记录确认其改动来源。

## 下一步核验清单

- [ ] 获取与该 APK 对应的完整修改后 Android Studio 源码。
- [ ] 确认 WAV/FLAC 输出、恢复日志和临时文件处理的实际实现。
- [ ] 确认 RAM 临时存储的准确含义、内存限制和持久化策略。
- [ ] 补齐简体中文资源并核对所有界面。
- [ ] 构建非 Debug 的 Release APK。
- [ ] 使用正式发布密钥签名并验证签名。
- [ ] 在 Android 7+ 与较新 Android 设备上完成录制、恢复、存储空间不足、权限撤销和后台中断测试。
- [ ] 将对应源码提交与 APK Release tag 绑定。
