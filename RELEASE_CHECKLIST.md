# V0.3 发布与分发检查清单

本清单区分“当前 APK 可对外提供体验”和“正式稳定版发行”。两者标准不同。

## 当前 V0.3 阶段版本状态

| 项目 | 状态 | 说明 |
|---|---|---|
| Debug APK 构建 | 已完成 | `:app:assembleDebug` 成功 |
| JVM 单元测试 | 已完成 | 41/41 通过 |
| 真机实际测试 | 已完成（维护者确认） | 整体使用未发现重大问题；逐项设备记录尚未归档 |
| APK 完整性与对齐 | 已完成 | ZIP、zipalign（含 16 KB 检查）和 APK v2 签名校验通过 |
| APK 对外体验分发 | 可进行 | 分发时应明确标注 V0.3 Debug 构建及其限制 |
| 对应完整源码 ZIP 上传 | 待完成 | 正确源码包 SHA 见 [SOURCE_ARCHIVE.md](SOURCE_ARCHIVE.md) |
| 真机测试记录归档 | 待补充 | 设备型号、Android 版本、测试场景和结果 |
| Lint | 未通过 | 257 errors / 1083 warnings / 1 hint |
| 完整 SBOM 与许可证映射 | 待完成 | 见 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) |
| 正式 Release variant | 待完成 | 当前 APK 是 Debug 构建，`debuggable=true` |
| 正式签名 | 待完成 | 当前证书为 Android Debug，不是项目正式发布证书 |

## 当前 APK 对外分发时必须说明

- 构建类型：V0.3 Debug。
- SHA-256：`d24bfd3ec0e6f25ca59d50831319ec461e29315ade60628f6f2860918469e0f5`。
- ABI：仅 arm64-v8a。
- Manifest：`debuggable=true`。
- 签名：Android Debug；与上游原作者签名版不同，不能直接覆盖安装。
- 真机测试：维护者已确认完成，整体无重大问题；但逐项测试明细尚未纳入仓库。

请勿把 Debug 签名 APK 描述为已正式签名的稳定 Production Release。当前阶段 APK 可以用于体验分发和反馈收集，但这不代表所有正式发行审查均已完成。

## 正式稳定版发布前

- [ ] 从准确源码基线构建 Release variant。
- [ ] 确认 `debuggable=false`，并核验最终 APK 签名。
- [ ] 由项目所有者安全保管正式签名密钥；绝不提交 keystore、密码或私钥。
- [ ] 制定与上游区分清楚的版本号策略。
- [ ] 处理 Lint 错误并记录豁免理由（如确有必要）。
- [ ] 归档设备型号、Android 版本、测试流程、逐项结果和可公开的测试证据。
- [ ] 完成第三方组件 SBOM 与许可证义务核查。
- [ ] 上传与最终 APK 精确对应的源码、修改记录和构建说明。
- [ ] 在同一 Release 中列出 APK、源码包 SHA-256、签名信息和变更说明。
