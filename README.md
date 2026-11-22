# CaptureCap-zh

**CaptureCap 的非官方中文增强版本。** 本仓库用于记录本项目的汉化、功能改动、构建来源、版本发布与第三方许可证信息。

> 本项目不是 CaptureCap 官方发行版。上游项目： [yepgoryo/CaptureCap](https://github.com/yepgoryo/CaptureCap)，上游作者：**Egor Yakovlev**。本改版的汉化及改版署名：**Di dh D'HDrd**。本项目与上游官方版本相互独立，请勿混淆。

## 项目状态

目前仓库已建立，正在整理首个公开版本。当前可确认的材料包括项目说明、上游 MIT 许可证文本，以及从现有 APK 中提取的部分第三方许可证文本。

**重要：目前尚未提交完整的修改后 Android Studio 源代码。** 因此本仓库暂时不是可复现构建的完整源码仓库；在源码、依赖版本和构建流程补齐前，不应声称任何人都能从仓库重建现有 APK。

## 改版内容

以下是本项目的改版方向，具体功能是否包含在某个 APK 中，应以对应版本的发布说明和测试记录为准：

- 中文本地化；
- RAM 临时存储；
- FLAC 无损音频录制。

这里的“FLAC 无损”指 FLAC 对输入 PCM 音频进行无损编码，不意味着能够恢复录音源头已经丢失的音质。

## 下载

APK 将通过 [GitHub Releases](https://github.com/q15040934511-commits/CaptureCap-zh/releases) 发布，不放入源码目录，也不提交进 Git 历史。每个版本应附带版本号、变更说明、SHA-256 校验值，以及与该 APK 对应的源码或源码获取方式。

## 仓库结构

```text
.
├── README.md
├── LICENSE
├── CHANGELOG.md
├── THIRD_PARTY_NOTICES.md
├── PRIVACY.md
├── RELEASE_NOTES.md
└── licenses/
```

## 上游项目与许可证

CaptureCap 上游项目及其 MIT 许可证声明见 [上游仓库](https://github.com/yepgoryo/CaptureCap)。根目录的 `LICENSE` 保留了从当前 APK 中提取到的上游 MIT 许可证文本。

当前 APK 还包含 GPL、LGPL 和 Xiph 许可证文本。它们具体对应哪些组件、版本和链接方式，仍需结合实际构建依赖及匹配源码核实。请先阅读 [第三方组件与许可证说明](THIRD_PARTY_NOTICES.md)。**不能将整个 APK 简单描述为仅受 MIT 许可证约束。**

## 隐私与安全

本项目尚未完成完整的权限、网络行为、遥测和数据存储审计。当前不能承诺应用完全离线或不收集数据。详情见 [隐私说明](PRIVACY.md)。

## 贡献与问题反馈

欢迎通过 GitHub Issues 提交可复现的问题、翻译建议和功能建议。提交问题时请注明：

- APK 版本号；
- Android 版本与设备型号；
- 复现步骤；
- 预期结果与实际结果；
- 相关日志或截图（请先移除个人信息）。

## 致谢

感谢 Egor Yakovlev 及 CaptureCap 上游项目的工作，也感谢所有相关开源依赖的维护者。
