# V0.3 源码包指纹与基线说明

## 已核验的完整源码包

- 文件名：`CaptureCap_HiFi_下一轮整改_V0.3_完整源码.zip`
- 大小：14,154,868 bytes
- SHA-256：`e410f10fe59cb53105932d745d4945066c057eee69f1c279650c22c707ceaf03`
- ZIP 完整性：本次重新运行 `unzip -t`，所有条目通过。
- 工程结构：包含 `gradlew.bat`、`settings.gradle.kts`、`app/build.gradle.kts` 等 Android Studio/Gradle 工程文件，共 890 个归档条目。

该 SHA 与构建报告指定的 V0.3 源码基线一致。这是可供解压、检查和构建的完整工程 ZIP，不是将 APK 再压缩得到的文件。

## 不要混用相似文件名

另有名称相近的源码 ZIP，SHA-256 不同。请只使用上述文件及 SHA，不要混用其他 V0.3 ZIP。

## GitHub 仓库上传状态

**当前仓库尚未包含上述二进制源码 ZIP。** 本次已将其校验信息和目标路径记录在仓库的 `source/README.md` 与 `source/SHA256SUMS.txt`。

目标仓库路径：

`source/CaptureCap_HiFi_下一轮整改_V0.3_完整源码.zip`

需要将经过 SHA-256 核验的原始 ZIP 上传到该路径。GitHub 自动生成的 Source code ZIP/tar.gz 是仓库提交快照，不等同于此 Android Studio 完整工程。

## 版本与构建绑定

V0.3 Debug APK SHA-256：

`d24bfd3ec0e6f25ca59d50831319ec461e29315ade60628f6f2860918469e0f5`

源码包 SHA 与 APK SHA 应在同一 Release 说明中列出。后续任何源码修改都应产生新提交、新构建和新 APK 哈希，不能沿用旧证据。
