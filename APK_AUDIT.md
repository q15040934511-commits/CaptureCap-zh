# APK 静态核验与测试状态报告

本报告区分用户最初提供的原版 `base.apk` 与 V0.3 构建产物。静态检查、构建日志和维护者反馈分别记录，不将三者混为同一种证据。

## 1. 原版 base.apk

| 项目 | 值 |
|---|---|
| 文件名 | `base.apk` |
| 文件大小 | 29,852,405 bytes |
| SHA-256 | `5516659bf10d01319f09e4dad68d7132caca6899155dfbe8f5ac303fbc3d4f53` |
| Application ID | `com.yepgoryo.CaptureCap` |
| versionName / versionCode | `3.9.8.8 / 46` |
| minSdk / targetSdk | 24 / 37 |
| ABI | arm64-v8a、armeabi-v7a、x86、x86_64 |
| DEX | 3 |
| 签名 | APK v2；证书 CN=Egor Yakovlev；SHA-256 `500d116f72635bf4e9172718e126ba4e09184599dbf69cddcb6c52a84478c8a6` |
| Hi-Fi 新增类 | 未发现 `HighFidelityAudioCapture`、`WavPcm16Writer`、`FlacPcm16Writer` |

结论：这是原作者签名的上游原版 APK，可作为原版行为对照；不是本项目 V0.3 改版 APK。

## 2. V0.3 Debug APK

| 项目 | 值 |
|---|---|
| 文件名 | `CaptureCap_HiFi_V0.3_debug_arm64.apk` |
| 文件大小 | 30,597,172 bytes |
| SHA-256 | `d24bfd3ec0e6f25ca59d50831319ec461e29315ade60628f6f2860918469e0f5` |
| Application ID | `com.yepgoryo.CaptureCap` |
| versionName / versionCode | `3.9.8.8 / 46` |
| minSdk / targetSdk | 24 / 37 |
| ABI | 仅 arm64-v8a |
| DEX | 7 |
| 签名 | APK v2；证书 CN=Android Debug；SHA-256 `5d79522a8f61b84f8d775121a12edbd6da49cb9d46f2d8dd31f1e27e25fcc63e` |
| Manifest | `android:debuggable=true` |
| DEX 构建模式 | `compilation-mode=debug` |

构建证据记录：ZIP 完整性检查通过，zipalign 常规与 16 KB 检查通过，apksigner v2 校验通过。该 APK 是可安装和体验的 Debug 构建，但不是使用正式发布密钥签名的 Release variant。它不能覆盖安装在设备上的原作者签名版；签名不一致时 Android 会拒绝更新安装。

## 3. 源码与 APK 对应关系

构建报告记录的 V0.3 源码 ZIP：
- 文件名：`CaptureCap_HiFi_下一轮整改_V0.3_完整源码.zip`
- SHA-256：`e410f10fe59cb53105932d745d4945066c057eee69f1c279650c22c707ceaf03`

该 SHA 与当前留存源码包实际计算值一致；构建报告同时记录了对应 APK 的 SHA-256。另有一个名称相近的 `CaptureCap高保真录音源码_V0.3.zip`，其 SHA 为 `1c6ebd8530c2cd8bb004b7d7e6156cef1e75b67ece664ffce0a2cd5297fb66b2`，**不等于构建报告指定的源码基线**，不要将两份 ZIP 混用。详见 [SOURCE_ARCHIVE.md](SOURCE_ARCHIVE.md)。

## 4. 功能静态线索与边界

V0.3 DEX/源码中存在：
- `HighFidelityAudioCapture`
- `PcmCapturePipeline`
- `WavPcm16Writer` / `FlacPcm16Writer`
- `LosslessSessionJournal`
- WAV/FLAC PCM16 输出和中断 Session 标记/恢复相关逻辑

以上是代码层面的核验结果。

### 中文本地化

匹配构建源码中存在 `values-zh-rCN/strings.xml`。按当前构建源码 XML 直接统计：
- 默认 `values/strings.xml`：314 个 `<string>` 项；
- `values-zh-rCN/strings.xml`：181 个 `<string>` 项；
- 仍缺少 133 个对应 string key。

所以当前应描述为**部分简体中文本地化**，不能称为完整汉化。构建 Lint 的 214 个 MissingTranslation 是全工程多语言缺失统计，不等于单独的中文缺失数量。

### RAM 临时存储

在匹配 V0.3 源码中未找到可确认的“所有录制数据仅存 RAM”的用户可选模式。PCM 队列、音频缓冲区和临时 Session 文件不等于 RAM-only 存储。当前不应把 RAM 临时存储宣传为已实现功能。

## 5. 构建与测试状态

- `:app:assembleDebug`：成功。
- `:app:testDebugUnitTest`：41 tests，0 failures，0 skipped。
- `:app:lintDebug`：失败，257 errors / 1083 warnings / 1 hint。
- **真机实际测试：项目维护者已确认完成，整体使用未发现重大问题。** 该状态根据维护者最新反馈记录。
- 当前归档材料尚未包含测试设备型号、Android 版本、各测试项的逐项结果、测试时长或原始录音/日志，因此不把未提供的细项写成独立 PASS，也不声称这些记录已由本仓库独立复核。

详细说明见 [BUILD_REPORT.md](BUILD_REPORT.md) 和 [TEST_REPORT.md](TEST_REPORT.md)。

## 6. 后续版本建议

1. 若继续对外分发当前 APK，保留“V0.3 Debug 构建”标识，并明确 Debug 签名、`debuggable=true` 和 arm64-v8a 限制。
2. 后续正式发行时构建 Release variant，确认 `debuggable=false，由项目所有者安全保管并使用正式签名密钥。
3. 决定版本号策略，避免沿用与上游相同的 3.9.8.8 / 46 造成误解。
4. 补齐部分中文翻译并处理 Lint 错误。
5. 将真机测试设备、系统版本、测试场景和结果归档，便于其他用户复核。
6. 完成第三方组件 SBOM 与许可证义务核查。
7. 将准确的 V0.3 源码包上传到 GitHub，并把 APK Release 与对应源码绑定。
