# Detail

## 这一层做什么
`bundles/` 是用户可见文案的唯一权威来源。这里同时维护默认语言和简体中文，覆盖设置标题、按钮文案、toast、角标配置说明、导入导出反馈等全部界面文本。

## 实现方式
- 文件遵守 Mindustry 设置命名规则，像 `setting.bhk-enabled.name`、`setting.bhk-show-icon-hotkeys.name` 这种 key 专门给设置菜单标题用。
- 另外一批 `bhk.*` key 供运行时对话框和提示文本调用，例如 `bhk.display.*`、`bhk.ignore.*`、`bhk.toast.banned`。
- Java 代码中几乎所有面向玩家的字符串都通过 `Core.bundle.get/format/getOrNull` 读取这里，符合仓库“用户可见文案不硬编码”的约束。

## 与其他层级的关系
- 上游是手写资源；下游会先复制到 `build/resources/main/bundles/`，再进入发布包。
- 它与 `BetterHotKeyFeature.java` 的设置 key、对话框标题和 toast 调用保持强耦合，改 key 时两边必须同步。
## 当前快照
- 直接文件数：2；直接子目录数：0；直接文件总大小：5011 字节。
- 直接文件类型：.properties x2。
- 直接文件示例：bundle_zh_CN.properties，bundle.properties。
- 直接子目录示例：无直接子目录。
