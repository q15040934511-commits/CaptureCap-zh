# 上游来源与基线

本项目基于以下上游项目开展：

- 项目：CaptureCap
- 仓库：https://github.com/yepgoryo/CaptureCap
- 上游作者：Egor Yakovlev
- 上游许可证：MIT（见本仓库根目录 `LICENSE`）
- 上游当前 main 分支核验提交：`c647f9fdb4409a950e913e50ed0d22b7944165db`
- 上游提交日期：2026-11-09

## APK 与上游版本字段

当前检查的 APK 为 `com.yepgoryo.CaptureCap`、versionName `3.9.8.8`、versionCode `46`。上游 main 分支的 `app/build.gradle.kts` 中这些字段及 minSdk 24、targetSdk 37、compileSdk 37 与 APK 对应。版本字段相同只说明元数据对应，不足以证明 APK 与某个上游提交完全一致。

## 上游维护状态

上游 README 已标注 Maintenance-Only Mode。上游的 `MAINTENANCE.md` 表示新功能不再优先，主要关注已报告的 bug；上游作者也在文档中说明其资源转向其他项目，并披露部分代码曾由 AI 辅助开发。请阅读上游原文：

- README：https://github.com/yepgoryo/CaptureCap
- Maintenance：https://github.com/yepgoryo/CaptureCap/blob/main/MAINTENANCE.md
- AI disclosure：https://github.com/yepgoryo/CaptureCap/blob/main/AI.md
- 上游发布页：https://github.com/yepgoryo/CaptureCap/releases

本项目应保留上游版权、许可和来源链接，并清楚区分上游已有内容与本项目新增/修改内容。不得暗示本项目是上游官方发行版，也不得把未审计的上游代码改动描述为本项目原创。

## 改版贡献记录

改版署名：Di dh D'HDrd。

后续每个版本应在 `CHANGELOG.md` 中单独标记：
- 上游同步内容；
- 本项目新增功能；
- 本项目修改或修复；
- 尚未验证或存在限制的功能。
