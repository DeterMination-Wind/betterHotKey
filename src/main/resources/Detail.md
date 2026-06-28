# Detail

## 这一层做什么
`src/main/resources/` 存放运行时资源。对于这个模组来说，资源层几乎等同于国际化层，因为这里只有 `bundles/`。

## 实现方式
- 没有图片、音频、着色器等资源，说明 betterHotKey 的用户界面完全依赖 Mindustry 原生控件和文本注入完成。

## 与其他层级的关系
- 向上被 `sourceSets.main.output` 收集。
- 向下 `bundles/` 为 Java 代码里的 `Core.bundle.get(...)` 提供键值。
## 当前快照
- 直接文件数：0；直接子目录数：1；直接文件总大小：0 字节。
- 直接文件类型：无直接文件。
- 直接文件示例：无直接文件。
- 直接子目录示例：bundles。
