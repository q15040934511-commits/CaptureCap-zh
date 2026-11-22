# v1.0.0 Release 页面更正说明

本文用于更正当前公开 Release 描述中与 V0.3 审计结果不一致的内容。**请以本文与仓库中的 APK 审计、构建和测试报告为准。**

## 需要更正的旧描述

此前 Release 描述列出了“中文界面本地化”和“RAM 临时存储功能”：

- **中文本地化：部分完成。** 与 V0.3 构建源码对应的默认 strings 有 314 项，简体中文资源有 181 项，仍缺少 133 个对应 key。因此不能写成完整汉化。
- **RAM-only 录制：未能证实。** 在已核对的 V0.3 源码中，没有找到可确认的“全部录制数据仅存 RAM”用户模式。不要把它列为已实现功能。
- **WAV/FLAC：** 源码中存在 WAV/FLAC PCM16 录制实现。FLAC 对输入 PCM 数据进行无损编码，不代表能恢复录制源头已经丢失的音质。

## 当前 Release 资产身份

Release tag：`v1.0.0`

Release 标题：`CaptureCap-zh-v1.0.0.apk`

注意：Release tag/标题是 GitHub 发布页的标识；APK 内部仍报告 `versionName=3.9.8.8`、`versionCode=46`。不要将 GitHub 标签误认为 APK 内部版本字段。

### APK 资产：`base.apk`

- 大小：30,597,172 bytes
- SHA-256：`d24bfd3ec0e6f25ca59d50831319ec461e29315ade60628f6f2860918469e0f5`
- 包名：`com.yepgoryo.CaptureCap`
- ABI：仅 arm64-v8a
- 签名：Android Debug
- Manifest：`debuggable=true`

维护者已确认 V0.3 真机实际测试完成，整体使用未发现重大问题；但设备型号、Android 版本和逐项测试记录尚未归档。因此当前应称为 V0.3 Debug 阶段体验构建，不应称为已完成正式签名和全部发布审查的稳定版。

### ZIP 资产：`CaptureCap-zh-v1.0.0.zip`

- 大小：30,597,318 bytes
- SHA-256：`73a4f3c91e2ecf459582617226f00add09c07d91c00529d213a1ca2c8cd9dc66`
- 内容性质：APK 的 ZIP 包装副本，不是 Android Studio 完整源码工程。

**不要把这个 ZIP 当成源码包，也不要用它替代下方列出的完整源码归档。**

### 真正的 V0.3 Android Studio 完整源码包

- 文件名：`CaptureCap_HiFi_下一轮整改_V0.3_完整源码.zip`
- 大小：14,154,868 bytes
- SHA-256：`e410f10fe59cb53105932d745d4945066c057eee69f1c279650c22c707ceaf03`
- ZIP 条目：890
- 完整性：`unzip -t` 通过

**截至本文更新时，该完整源码 ZIP 尚未提交到本仓库。** 计划路径为：

`source/CaptureCap_HiFi_下一轮整改_V0.3_完整源码.zip`

## 可直接替换到 GitHub Release 的描述

以下文本不包含尚未证实的功能承诺：

---

CaptureCap-zh · V0.3 阶段体验构建

这是基于 CaptureCap 的非官方中文增强版本，与上游作者及官方项目没有隶属关系。

### 本版本状态

- WAV/FLAC PCM16 录制实现已纳入当前源码。
- 项目维护者确认已完成真机实际测试，整体使用未发现重大问题。
- 简体中文本地化仍未完成，当前为部分本地化。
- RAM-only 录制模式尚未得到源码核实，不作为本版本已实现功能宣传。
- 当前 APK 是 Debug 构建，不是正式签名的 Production Release。

### 下载资产

- `base.apk`：V0.3 Debug APK；仅 arm64-v8a。
- `CaptureCap-zh-v1.0.0.zip`：APK 的 ZIP 包装副本，不是完整源码。

APK SHA-256：

`d24bfd3ec0e6f25ca59d50831319ec461e29315ade60628f6f2860918469e0f5`

APK 内部版本：`3.9.8.8 (46)`。GitHub Release tag `v1.0.0` 不会改变 APK 内部版本字段。

### 安装提示

当前 APK 使用 Android Debug 签名，与上游原作者签名版不同，不能直接覆盖安装。安装前请备份重要数据，不要为了安装测试构建而贸然卸载已有应用。

### 项目来源与许可证

上游项目：Egor Yakovlev / CaptureCap  
https://github.com/yepgoryo/CaptureCap

本项目为非官方改版。上游和第三方组件的版权声明与许可证继续保留。不同组件可能采用不同许可证，不能把整个 APK 简化标注为“仅 MIT”。

---

更详细的技术信息见仓库中的 `README.md`、`APK_AUDIT.md`、`BUILD_REPORT.md`、`TEST_REPORT.md`、`THIRD_PARTY_NOTICES.md` 和 `SOURCE_ARCHIVE.md`。
