# 当前 APK 发布核验记录

**状态：不适合直接作为正式公开 Release。**

## 文件信息

- 原始文件名：`base.apk`
- 文件大小：30,597,172 bytes
- SHA-256：`d24bfd3ec0e6f25ca59d50831319ec461e29315ade60628f6f2860918469e0f5`
- Application ID：`com.yepgoryo.CaptureCap`
- versionName：`3.9.8.8`
- versionCode：`46`
- minSdk：`24`
- targetSdk：`37`

## 阻止发布的原因

- Manifest 含 `android:debuggable=true`。
- DEX 标记为 Debug 编译模式。
- APK 由 Android Debug 自签名证书签署，不是可用于公开长期更新的项目 Release key。
- 完整修改后源码尚未入库，无法复现构建。
- 中文资源尚未确认。
- RAM 临时存储行为尚未完成核验。
- 尚未完成设备回归测试与第三方组件 SBOM。

## 下一版正式 Release 的前置条件

1. 从完整修改后源码执行 Release 构建。
2. 确认 Manifest 不可调试，并验证 APK 签名。
3. 安全保存项目发布密钥，私钥不得上传 GitHub。
4. 完成 WAV/FLAC、录音、存储空间不足、临时 session 恢复、权限撤销及后台中断测试。
5. 确认中文翻译和 RAM 临时存储功能的实际表现。
6. 补齐匹配源码、构建说明和第三方组件清单。
7. 更新版本号、变更日志和 SHA-256 后再创建公开 Release。

## 当前文件 SHA-256

`d24bfd3ec0e6f25ca59d50831319ec461e29315ade60628f6f2860918469e0f5`
