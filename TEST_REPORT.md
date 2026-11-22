# CaptureCap Hi-Fi V0.3 功能测试报告

## 总结

**当前没有 Android 真机运行测试通过记录。** 构建环境没有连接设备，`/dev/kvm` 不存在，模拟器多次启动失败。因此所有设备侧测试均为 NOT RUN。

## 已完成的非真机验证

- JVM 单元测试：41 tests，0 failures，0 skipped。
- 单独的生命周期屏障测试：8 项 PASS。
- FLAC Writer/Decoder、WAV Writer、PCM 队列、Session Journal 等 JVM 测试已执行。
- 源码静态检查确认 AAC/M4A 路线仍保留，WAV/FLAC 使用 PCM 管线。

以上结果不等同于 Android 真机录音验收。

## 真机测试矩阵

| 类别 | 内容 | 状态 |
|---|---|---|
| A | 原版 AAC/M4A 录制、暂停恢复、连续录制 | NOT RUN |
| B | SAF 文件夹选择、WAV/FLAC 导出、复制失败恢复 | NOT RUN |
| C | WAV/FLAC 20 分钟与 30 分钟长录音、暂停恢复 | NOT RUN |
| D | 快速停止、重复停止、Session 竞态 | NOT RUN |
| E | 低存储空间、强制结束进程、Journal 恢复 | NOT RUN |
| F | AudioRecord 采样率、声道回退、设备兼容 | NOT RUN |

未生成可供核验的真机录音文件，因此没有真机文件时长、采样率、声道、解码和文件完整性结论。

## 已知限制

1. `lintDebug` 失败：257 errors / 1083 warnings / 1 hint。
2. 20/30 分钟 WAV/FLAC 真机长录音尚未测试。
3. AAC/M4A 与 SAF 真机回归尚未测试。
4. 暂停/恢复、快速启停、强杀恢复尚未测试。
5. 设备差异、实际 AudioRecord 输入能力和输出文件播放兼容性尚未测试。

## 结论

V0.3 当前状态是：**Debug 构建成功、JVM 单测通过、Lint 未通过、真机功能测试未执行**。不得将其宣传为稳定正式版或真机验收通过版本。
