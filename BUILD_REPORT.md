# CaptureCap Hi-Fi V0.3 构建报告

本报告依据 V0.3 构建证据包中的构建日志摘要整理。它记录的是构建环境结果，不代表 Android 真机功能验收。

## 构建环境

| 项目 | 记录 |
|---|---|
| OS | Ubuntu 22.04.5 LTS |
| JDK | Oracle JDK 17.0.2 |
| Gradle Wrapper | 9.6.0 |
| Android Gradle Plugin | 9.4.1 |
| Kotlin | 2.2.10 |
| compileSdk / targetSdk / minSdk | 37 / 37 / 24 |
| NDK | 27.0.12077973 |
| 真机 | 无；adb devices 为空 |
| 虚拟化 | 无 /dev/kvm，模拟器未成功启动 |

## 构建输入

- 源码包：`CaptureCap_HiFi_下一轮整改_V0.3_完整源码.zip`
- SHA-256：`e410f10fe59cb53105932d745d4945066c057eee69f1c279650c22c707ceaf03`
- 构建报告记录的基线提交：`448ac62 baseline: V0.3 source zip e410f10f`
- 构建过程中只添加本机 `local.properties`，未修改核心源码。

## 任务结果

| 任务 | 退出码 | 结果 |
|---|---:|---|
| `./gradlew --version` | 0 | Gradle 9.6.0 / JVM 17.0.2 |
| `:app:assembleDebug` | 0 | BUILD SUCCESSFUL，3m 11s |
| `:app:testDebugUnitTest` | 0 | BUILD SUCCESSFUL，41 tests / 0 failures / 0 skipped |
| `:app:lintDebug` | 1 | BUILD FAILED，257 errors / 1083 warnings / 1 hint |

Lint 错误类型统计：MissingTranslation 214、NewApi 23、Orientation 11、MissingPermission 4、MissingPrefix 2、WrongConstant 2、PermissionImpliesUnsupportedChromeOsHardware 1。Lint 没有被禁用或绕过。

## APK 产物

| 项目 | 值 |
|---|---|
| 文件 | `CaptureCap_HiFi_V0.3_debug_arm64.apk` |
| 大小 | 30,597,172 bytes |
| SHA-256 | `d24bfd3ec0e6f25ca59d50831319ec461e29315ade60628f6f2860918469e0f5` |
| 包名 | `com.yepgoryo.CaptureCap` |
| versionName / versionCode | `3.9.8.8 / 46` |
| ABI | arm64-v8a only |
| DEX | 7 |
| 签名 | APK v2；CN=Android Debug |
| Manifest | `debuggable=true` |
| ZIP 完整性 | 通过 |
| zipalign | 常规与 16 KB 检查通过 |

此 APK 是 Debug 构建，不是正式发布包。JVM 单元测试通过也不代表 Android 系统录音、SAF 或长时间录制在真机上通过。

## 证据边界

详细原始日志、JUnit XML、Lint 结果、APK 签名和对齐检查记录位于项目构建证据包。当前 GitHub 仓库记录的是可读摘要；不能把摘要当作完整原始日志。
