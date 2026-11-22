# APK 与 Release 状态核验记录

**当前状态：公开 GitHub Release 已创建并提供 V0.3 APK。项目维护者已确认真机实际测试完成，整体使用未发现重大问题。该 APK 仍是 Debug 构建，不是正式发布密钥签名的 Release variant。**

## GitHub Release 信息

- Release tag：`v1.0.0`
- Release 标题：`CaptureCap-zh-v1.0.0.apk`
- APK 资产：`base.apk`
- 另一个 ZIP 资产：`CaptureCap-zh-v1.0.0.zip`，其内容是 APK 的 ZIP 包装副本，不是 Android Studio 完整源码。

GitHub Release tag 和标题属于仓库发布页标识，不会改变 APK 内部版本字段。当前 APK 仍为 `versionName=3.9.8.8`、`versionCode=46`。Release 描述中 RAM-only 与完整中文本地化的旧说法需要更正，详见 [RELEASE_CORRECTION.md](RELEASE_CORRECTION.md)。

## A. 原版 base.apk（对照包）

- 文件大小：29,852,405 bytes
- SHA-256：`5516659bf10d01319f09e4dad68d7132caca6899155dfbe8f5ac303fbc3d4f53`
- Application ID：`com.yepgoryo.CaptureCap`
- versionName / versionCode：`3.9.8.8 / 46`
- 签名：CN=Egor Yakovlev，原作者签名
- ABI：arm64-v8a、armeabi-v7a、x86、x86_64

这是原版对照包，不是本项目 V0.3 改版 APK。

## B. V0.3 Debug APK

- 文件名：`base.apk`（GitHub Release 资产名）
- 文件大小：30,597,172 bytes
- SHA-256：`d24bfd3ec0e6f25ca59d50831319ec461e29315ade60628f6f2860918469e0f5`
- Application ID：`com.yepgoryo.CaptureCap`
- versionName / versionCode：`3.9.8.8 / 46`
- ABI：仅 arm64-v8a
- 签名：CN=Android Debug；APK Signature Scheme v2
- Manifest：`debuggable=true`

ZIP 完整性、zipalign 和 v2 签名校验通过。该 APK 是可安装和体验的 Debug 构建，但不是使用正式发布密钥签名的 Release variant。它不能覆盖安装在设备上的原作者签名版；该构建也不应被描述为正式签名 Release。

## C. Release 中的 ZIP 资产

- 文件名：`CaptureCap-zh-v1.0.0.zip`
- 文件大小：30,597,318 bytes
- SHA-256：`73a4f3c91e2ecf459582617226f00add09c07d91c00529d213a1ca2c8cd9dc66`
- 内容：APK 的 ZIP 包装副本，并非完整 Android Studio 项目源码。

不要将这个文件当成源码包。

## D. 对应源码基线

构建证据指定的源码包：

`CaptureCap_HiFi_下一轮整改_V0.3_完整源码.zip`

SHA-256：

`e410f10fe59cb53105932d745d4945066c057eee69f1c279650c22c707ceaf03`

该源码包 SHA 已与构建证据核对一致。注意不要使用名称相近但 SHA 不同的另一份 V0.3 ZIP。**此完整源码包尚未上传到本 GitHub 仓库**，详见 [SOURCE_ARCHIVE.md](SOURCE_ARCHIVE.md)。

## E. 构建与测试结果

- assembleDebug：成功。
- JVM 单元测试：41/41 通过。
- lintDebug：失败，257 errors / 1083 warnings / 1 hint。
- 真机实际测试：维护者确认已完成，整体无重大问题；设备与逐项测试明细尚未归档。

## F. 后续正式发行建议

1. 如继续分发当前 APK，应保留 V0.3 Debug 构建标识，并展示 SHA-256、签名信息与 ABI 范围。
2. 后续正式发行时构建 Release variant，确认 `debuggable=false`，并使用项目所有者安全保管的正式签名密钥。
3. 不要上传 keystore、签名私钥、密码或访问令牌。
4. 补齐中文资源并处理 Lint 错误。
5. 将真机设备、系统版本、测试场景和结果归档。
6. 核对 SBOM、第三方许可证及相应源码提供义务。
7. 上传准确的对应源码，并把 APK 与源码基线绑定到同一 Release。
