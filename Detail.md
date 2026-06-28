# Detail

## 这一层做什么
仓库根目录是整个 betterHotKey 模组的真正控制面。这里同时放着源码入口、Gradle 构建脚本、Mindustry 模组元数据、用户文档、需求记录，以及三类产物目录：`build/` 是 Gradle 中间输出，`dist/` 是当前可直接发布的合并包，`构建/` 是按版本归档的历史发布副本。

## 实现方式
- `build.gradle` 定义了 Java 8 兼容、MindustryJitpack 依赖、D8 查找逻辑、桌面/Android/合并包任务、以及把产物复制到 `dist/` 和 `构建/betterHotKey/` 的流程。
- `mod.json` 声明模组身份：`name=betterhotkey`、`version=1.1.0`、`main=betterhotkey.BetterHotKeyMod`、`minGameVersion=154`、`hidden=true`、`java=true`。游戏真正加载的是这里指向的主类。
- `README.md` 解释 v1.1.0 的用户可见功能，包括角标显示、字号调节、忽略地形后的编号修正，以及为 Neon 预留的 `bekBundled / bekBuildSettings` 接口。
- `feedback.txt` 记录了本次功能来源：建筑图标右下角显示快捷键、被 ban 建筑保持原位后列数锁定的问题、以及自定义行列数诉求。它解释了为什么源码里会出现角标、列数配置和保序重排逻辑。

## 与其他层级的关系
- 上游没有更高一层的项目配置目录；这里就是 Gradle、Mindustry 和 GitHub Actions 读取的入口。
- `src/` 提供手写源码和多语言资源，是功能实现的唯一权威来源。
- `.github/` 把这里的构建约定搬到云端发布；`.gradle/` 与 `build/` 则把这里的脚本执行结果缓存到本地。
- `dist/` 与 `构建/` 都是从 `build.gradle` 定义的复制任务落盘出来的结果，其中 `dist` 强调“当前发布”，`构建` 强调“按版本留档”。
## 当前快照
- 直接文件数：6；直接子目录数：6；直接文件总大小：13117 字节。
- 直接文件类型：.gradle x2，.md x2，.json x1，.txt x1。
- 直接文件示例：AGENTS.md，build.gradle，feedback.txt，mod.json，README.md，settings.gradle。
- 直接子目录示例：.github，.gradle，构建，build，dist，src。
