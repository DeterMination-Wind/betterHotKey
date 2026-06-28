# src/main/java/betterhotkey/features 详细说明

目录路径：`src/main/java/betterhotkey/features`

## 本层定位
- 这一层是 betterHotKey 的真正引擎：组合热键、数字编号重映射、角标显示、配置对话框、OverlayUI 同步、反射访问 Placement UI，都集中在这里。

## 当前内容
- 直接子目录数：0。
- 直接文件数：1。
- 递归下级目录数：0。
- 递归文件数：1。
- 本层没有直接子目录。
- 直接文件：`BetterHotKeyFeature.java`。

## 实现方式
- `BetterHotKeyFeature` 用大量 `Core.settings` 键管理功能开关、显示颜色、字号、分组配置与忽略地形名单；同时维护编译后的按键绑定缓存，避免每帧重复解析。
- 它在 `Trigger.update` 与 `Trigger.uiDrawEnd` 分工运行：前者更新状态与输入，后者在原生逻辑跑完后补做编号重映射、角标绘制与 Overlay 刷新。
- 功能层还内置多个对话框和导入导出逻辑，把复杂配置持久化为 `Seq<String>` 文本协议，而不是另起单独文件。

## 与其他层级的关系
- 这里强依赖 Mindustry UI 内部字段和内容表，因此和游戏版本耦合度较高；入口层和 Neon 聚合层只是它的外壳。

## 本层文件解读
- `BetterHotKeyFeature.java`: Java source，Mod implementation source code.，大小 88.6 KB。 声明类型：BetterHotKeyFeature, CenteredCheckSetting, GroupConfig, BindingConfig, CompiledBinding；公开/受保护方法约 4 个，含 OverlayUI 集成

## 维护关注点
- 凡是涉及输入时序和 UI 反射的改动都容易回归，文档里需要明确它并不是普通设置页模块。
- 这一层更接近事实来源，做结构或行为调整应优先改这里，再通过构建链刷新下游。

## 层级关系速记
- 上层目录：`src/main/java/betterhotkey`。
- 下层入口：无。
- 当前文档由 `tools/generate_detail.py` 依据工作区实时结构与人工摘要生成。
