# APK 与 Release 状态核验记录

**当前状态：公开 GitHub Release 已创建并提供 V0.3 APK。项目维护者已确认真机实际测试完成，整体使用未发现重大问题。该 APK 仍是 Debug 构建，不是正式发布密钥签名的 Release variant。**

Release 资产显示名称为“基础.apk”，大小约 29.2 MiB；其 SHA-256 与构建记录中的 V0.3 Debug APK 一致。完整 SHA-256：

`d24bfd3ec0e6f25ca59d50831319ec461e29315ade60628f6f2860918469e0f5`

此前文档将原版 `base.apk` 与 V0.3 Debug APK 混为同一文件，现已更正。两个文件的大小、SHA-256 和签名不同，不能互换。

## A. 原版 base.apk

- 文件大小：29,852,405 bytes
- SHA-256：`5516659bf10d01319f09e4dad68d7132caca6899155dfbe8f5ac303fbc3d4f53`
- Application ID：`com.yepgoryo.CaptureCap`
- versionName / versionCode：`3.9.8.8 / 46`
- 签名：CN=Egor Yakovlev，原作者签名
- ABI：arm64-v8a、armeabi-v7a、x86、x86_64

这是原版对照包，不是本项目 V0.3 改版 APK。

## B. V0.3 Debug APK

- 构建产物文件名：`CaptureCap_HiFi_V0.3_debug_arm64.apk`
- Release 页面显示名称：`基础.apk`
- 文件大小：30,597,172 bytes
- SHA-256：`d24bfd3ec0e6f25ca59d50831319ec461e29315ade60628f6f2860918469e0f5`
- Application ID：`com.yepgoryo.CaptureCap`
- versionName / versionCode：`3.9.8.8 / 46`
- ABI：仅 arm64-v8a
- 签名：CN=Android Debug；APK Signature Scheme v2
- Manifest：`debuggable=true`

ZIP 完整性、zipalign 和 v2 签名校验通过。项目维护者已确认该阶段 APK 完成真机实际测试，整体未发现重大问题。Debug 签名与原作者签名不同，因此不能覆盖安装在设备上的原作者签名版；该构建也不应被描述为正式签名 Release。

## C. 对应源码基线

构建证据指定的源码包：
`CaptureCap_HiFi_下一轮整改_V0.3_完整源码.zip`

SHA-256：
`e410f10fe59cb53105932d745d4945066c057eee69f1c279650c22c707ceaf03`

此源码包 SHA 已与构建证据核对一致。注意不要使用名称相近但 SHA 不同的另一份 V0.3 ZIP。源码包尚未上传到本 GitHub 仓库，详见 [SOURCE_ARCHIVE.md](SOURCE_ARCHIVE.md)。

## D. 构建与测试结果

- assembleDebug：成功。
- JVM 单元测试：41/41 通过。
- lintDebug：失败，257 errors / 1083 warnings / 1 hint。
- 真机实际测试：维护者确认已完成，整体无重大问题；设备与逐项测试明细尚未归档。

## E. 后续正式发行建议

1. 如继续分发当前 APK，应保留 V0.3 Debug 构建标识，并展示 SHA-256、签名信息与 ABI 范围。
2. 后续正式发行时构建 Release variant，确认 `debuggable=false)，并使用项目所有者安全保管的正式签名密钥。
3. 不要上传 keystore、签名私钥、密码或访问令牌。
4. 补齐中文资源并处理 Lint 错误。
5. 将真机设备、系统版本、测试场景和结果归档。
6. 核对 SBOM、第三方许可证及相应源码提供义务。
7. 上传准确的对应源码，并把 APK 与源码基线绑定到同一 Release。
