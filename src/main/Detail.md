# Detail

## 这一层做什么
`src/main/` 对应 Gradle 主源码集，是会进入最终模组包的全部手写内容集合。

## 实现方式
- `java/` 保存运行时代码。
- `resources/` 保存 bundle 资源。
- 这两个子层会在构建时分别进入 `build/classes/java/main/` 与 `build/resources/main/`。

## 与其他层级的关系
- 它是 `build.gradle` 中 `sourceSets.main` 的默认入口。
- 它之下的每个文件都直接决定最终发布物的行为。
## 当前快照
- 直接文件数：0；直接子目录数：2；直接文件总大小：0 字节。
- 直接文件类型：无直接文件。
- 直接文件示例：无直接文件。
- 直接子目录示例：java，resources。
