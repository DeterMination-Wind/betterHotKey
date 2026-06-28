# Detail

## 这一层做什么
`workflows/` 保存 GitHub Actions 工作流定义，是“仓库被打 tag 之后如何自动构建并上传 Release”的说明书。当前唯一文件 `release.yml` 已经覆盖手动触发和 `v*` 标签触发两种发布入口。

## 实现方式
- 工作流先 checkout 仓库，再安装 Temurin Java 17、Gradle 环境和 Android SDK/build-tools 34.0.0。Java 17 只是运行构建工具，真正字节码仍由 `build.gradle` 强制降到 Java 8。
- 构建步骤执行 `clean deploy`。这和仓库根的 Gradle 任务设计保持一致，意味着云端发布拿到的是合并后的 `.jar` 与 `.zip`，包含桌面 class、资源、`classes.dex` 与 `mod.json`。
- Release 阶段只上传 `dist/*.jar` 与 `dist/*.zip`，因此 `dist/` 是 CI 视角下的最终发布目录。

## 与其他层级的关系
- 它向上依赖根目录脚本约定；向下没有更细分目录。
- 它与 `dist/` 的关系最直接：工作流不关心 `build/` 的中间文件，只取 `dist/` 的最终结果。
## 当前快照
- 直接文件数：1；直接子目录数：0；直接文件总大小：1198 字节。
- 直接文件类型：.yml x1。
- 直接文件示例：release.yml。
- 直接子目录示例：无直接子目录。
