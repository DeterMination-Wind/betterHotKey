# src/main/java/betterhotkey 详细说明

目录路径：`src/main/java/betterhotkey`

## 本层定位
- 这是 betterHotKey 的入口层，负责把重型功能逻辑接到 Mindustry 生命周期，并在独立运行与被 Neon 打包之间切换设置注册策略。

## 当前内容
- 直接子目录数：2。
- 直接文件数：1。
- 递归下级目录数：2。
- 递归文件数：3。
- 直接子目录：`features`、`integration`。
- 直接文件：`BetterHotKeyMod.java`。

## 实现方式
- `BetterHotKeyMod` 只做薄入口：初始化 `BetterHotKeyFeature`，在 `ClientLoadEvent` 时根据 `bekBundled` 决定是否调用 `ui.settings.addCategory(...)`。
- 这种结构把 UI 注册与业务逻辑彻底拆开，便于 Neon 直接复用 `bekBuildSettings`，而不需要复制内部实现。

## 与其他层级的关系
- 它向下依赖 `features/` 与 `integration/`；向上被 `BekToolsMod` 作为一个组接入统一设置入口。

## 本层文件解读
- `BetterHotKeyMod.java`: Java source，Mod implementation source code.，大小 970 B。 声明类型：BetterHotKeyMod；公开/受保护方法约 2 个，含聚合设置入口; 含打包标记

## 维护关注点
- 入口层应保持薄，不要把真正的热键实现塞回这里。
- 这一层更接近事实来源，做结构或行为调整应优先改这里，再通过构建链刷新下游。

## 层级关系速记
- 上层目录：`src/main/java`。
- 下层入口：`features`、`integration`。
- 当前文档由 `tools/generate_detail.py` 依据工作区实时结构与人工摘要生成。
