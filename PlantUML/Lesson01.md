# PlantUML 基础

PlantUML 是一个程序库。它定义了一种标记语言，并提供了把这种语言书写的文本渲染为 UML 图的功能。一个什么都不显示的 PlantUML 文档应当是这样：

```PlantUML
@startuml MyUML
@enduml
```

`@startuml` 和 `@enduml` 是 PlantUML 文档的开始和结束标记。在这一对标记中间定义 UML 图的各种元素。`MyUML` 是图的名字，这是一个可选项。

如果要书写注释，可以在一行的开头加 `'`，例如：

```PlantUML
@startuml MyUML
' This is a comment.
@enduml
```

而一个简单的有可显示内容的 PlantUML 文本可以是这样：

```PlantUML
@startuml MyUML
Alice -> Bob: test
@enduml
```

你可以创建一个纯文本文件，把这些内容复制进去，重命名为以 `.plantuml` 后缀的名称。然后，用安装好插件的 Visual Studio Code 打开。按下 Alt + D 来预览图片。如果你要导出图片，可以使用 Ctrl + Shift + P 打开命令行输入命令：

```
PlantUML: Export Current File Diagrams
```

然后选择导出的格式。如果文档中有多对 `@startuml` 和 `@enduml` 标记，那么多张图片会一次性导出。