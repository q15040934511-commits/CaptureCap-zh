# APK 与 Release 状态核验记录

**当前状态：公开 GitHub Release 已创建，但其中上传的是 V0.3 Debug APK，不是正式稳定发行包。**

截图所示 Release 资产名为“基础.apk”，大小约 29.2 MB；其 SHA-256 前缀与构建记录中的 V0.3 Debug APK 一致。该 Debug APK 的完整 SHA-256 为：

`d24bfd3ec0e6f25ca59d50831319ec461e29315ade60628f6f2860918469e0f5`

此前文档将原版 `base.apk` 与 V0.3 Debug APK 混为同一文件，现已更正。两个文件的大小、SHA-256 和签名不同，不能互换。

## A. 原版 base.apk

- 文件大小：29,852,405 bytes
- SHA-256：`5516659bf10d01319f09e4dad68d7132caca6899155dfbe8f5ac303fbc3d4f53`
- Application ID：`com.yepgoryo.CaptureCap`
- versionName / versionCode：`3.9.8.8 / 46`
- 签名：CN=Egor Yakovlev，原作者签名
- ABI：arm64-v8a、armeabi-v7a、x86、x86_64

这是原版对照包，不是本项目 V0.3 改版发布包。

## B. V0.3 Debug APK

- 文件名：Release 页面显示为“基础.apk”；构建产物原名为 `CaptureCap_HiFi_V0.3_debug_arm64.apk`
- 文件大小：30,597,172 bytes
- SHA-256：`d24bfd3ec0e6f25ca59d50831319ec461e29315ade60628f6f2860918469e0f5`
- Application ID：`com.yepgoryo.CaptureCap`
- versionName / versionCode：`3.9.8.8 / 46`
- ABI：仅 arm64-v8a
- 签名：CN=Android Debug；仅 APK Signature Scheme v2
- Manifest：`debuggable=true`

ZIP 完整性、zipalign 和 v2 签名校验通过，但这不代表真机功能验收通过。它不能作为正式 Release，也不能覆盖安装在设备上的原作者签名版；签名不一致时 Android 会拒绝更新安装。

## C. 对应源码基线

构建证据指定的源码包为：
`CaptureCap_HiFi_下一轮整改_V0.3_完整源码.zip`

SHA-256：
`e410f10fe59cb53105932d745d4945066c057eee69f1c279650c22c707ceaf03`

此源码包 SHA 已与构建证据核对一致。注意不要使用名称相近但 SHA 不同的另一份 V0.3 ZIP。源码包尚未上传到本 GitHub 仓库，详见 [SOURCE_ARCHIVE.md](SOURCE_ARCHIVE.md)。

## D. 构建与测试结果

- assembleDebug：成功。
- JVM 单元测试：41/41 通过。
- lintDebug：失败，257 errors / 1083 warnings / 1 hint。
- Android 真机 A–F 测试：全部 NOT RUN。

因此，当前 Release 只能标注为内部测试构建，不应宣传为稳定正式版或真机验收通过版本。

## E. 正式发布前置条件

1. 从准确源码基线构建 Release variant。
2. 确认 `debuggable=false`，并验证正式签名。
3. 由项目所有者安全保管发布密钥，不要上传 keystore 或密码。
4. 补齐中文资源并处理 Lint 错误。
5. 完成 Android 真机回归测试。
6. 核对 SBOM、第三方许可证及相应源码提供义务。
7. 设定区别于上游的版本标识，生成 APK SHA-256。
8. 上传对应源码并将其与 APK Release tag 绑定。
