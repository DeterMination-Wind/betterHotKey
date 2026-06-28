# src/main/java/betterhotkey/integration 详细说明

目录路径：`src/main/java/betterhotkey/integration`

## 本层定位
- 这一层专门处理对 MindustryX OverlayUI 的弱耦合集成，目的是让主逻辑不被反射细节污染。

## 当前内容
- 直接子目录数：0。
- 直接文件数：1。
- 递归下级目录数：0。
- 递归文件数：1。
- 本层没有直接子目录。
- 直接文件：`MindustryXOverlayUI.java`。

## 实现方式
- 这里通常只包装窗口注册、启停和 pinned 同步所需的反射调用，保证外部组件不存在时能自然降级。

## 与其他层级的关系
- 它被 `features/BetterHotKeyFeature` 调用，本身不承担独立设置或事件初始化。

## 本层文件解读
- `MindustryXOverlayUI.java`: Java source，Mod implementation source code.，大小 4.3 KB。 声明类型：MindustryXOverlayUI；公开/受保护方法约 4 个，含 OverlayUI 集成

## 维护关注点
- 外部接口名变动时，优先改这一层而不是主业务层。
- 这一层更接近事实来源，做结构或行为调整应优先改这里，再通过构建链刷新下游。

## 层级关系速记
- 上层目录：`src/main/java/betterhotkey`。
- 下层入口：无。
- 当前文档由 `tools/generate_detail.py` 依据工作区实时结构与人工摘要生成。
