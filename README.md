# UML Lesson

Lessons for UML.

[Unified Modeling Language (UML)](https://en.wikipedia.org/wiki/Unified_Modeling_Language) 是一组建模语言。程序开发中的许多模型关系可以用这些语言进行表述。

UML 的具体实现有很多。既可以使用通用图表自己绘制也可以写标记语言然后通过软件渲染为 UML 的图。Visio， Draw.io 等属于前者， PlantUML， Mermaid 等属于后者。个人认为后者的实现方式更节约人力，所有更好。相比之下， PlantUML 对 UML 有更全面的支持，功能也更多，所以本教程主要介绍 PlantUML，也会介绍一些 Mermaid 实现的 UML。

> 相关资源
> * [UML.org](https://www.uml.org/) 是 UML 的官方网站，可以在上边下载 UML 标准说明文件。
> * [PlantUML](https://plantuml.com/en/) 是一个用标记语言制作图表的库，它支持大部分 UML 标准图表的描述和绘制。
> * [Mermaid](https://mermaid-js.github.io/mermaid/) 是一个用标记语言制作图表的库，其中实现了部分 UML 的图表类型。

## 基于 PlantUML 的课程

[《基于 PlantUML 的 UML 课程》目录](./PlantUML/README.md)

## 基于 Mermaid 的课程

[《基于 Mermaid 的 UML 课程》目录](./Mermaid/README.md)

## 其他

尽量使用有明确语义和严格语法的标记方式

目前感觉面向对象程序设计比较常用的图：

* 类图 （带枚举、接口等拓展）
* 对象图 （举例或者表示特殊对象）
* 包图 （对应命名空间）
* 借用组件图的棒棒糖表示类之间的接口调用关系（看看能不能稍微扩展一下以方法为起止点，用于表示方法调用关系）
* 新增的 Composite Structure Diagram 可以用于表述复杂类内部不同部分的关系（但是感觉语义不是很明确，也不是很常用）
* 使用拓展的 Profile Diagram 方式约定一些应当说明的内容（例如虚函数和重写）
* 流程图，泳道图可以用于说明复杂函数的实现或者复杂过程
* 状态图

需求分析可能用用例图

面向过程编程--状态图，流程图
面向对象编程--类图，对象图