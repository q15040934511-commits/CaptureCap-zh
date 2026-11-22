# 第三方组件与许可证说明

## 当前 APK 中直接观察到的许可证文件

- `META-INF/licenses/COPYING.GPL`：GNU GPL v2 许可证文本。
- `META-INF/licenses/COPYING.LGPL`：GNU LGPL v2.1 许可证文本。
- `META-INF/licenses/COPYING.Xiph`：Xiph.Org / Josh Coalson 版权声明及 BSD 风格条件。
- `assets/license.txt`：CaptureCap 上游 MIT 许可证文本，副本位于仓库根目录 `LICENSE`。

## 尚未确认的事项

仅凭 APK 内存在许可证文本，无法可靠判断每份许可证具体对应哪些二进制库、版本、代码路径、链接方式或修改内容。当前 APK 还包含 librtmp 相关 native 库和 scrcpy-server 资源；在取得匹配源码、依赖锁定文件和上游组件清单前，不在此处擅自指定它们的许可证。

## 发布前核查清单

1. 根据实际构建依赖逐项记录组件名称、版本、来源、许可证及其在 APK 中的对应文件。
2. 确认 GPL/LGPL 组件是否实际包含在发行物中，并满足适用的许可证义务，包括许可证副本、源码提供、修改标记及适用时的可重新链接材料。
3. 确认 Xiph 相关组件的版权声明、条件和免责声明得到保留。
4. 将准确的第三方源码、补丁或源码获取方式与对应 APK 版本绑定。
5. 不要把整个 APK 简化标注为“仅 MIT”。

这是一份基于当前 APK 文件内容的初步盘点，不是完整 SBOM，也不构成法律意见。
