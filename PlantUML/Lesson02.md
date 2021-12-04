# 类型元素的表示

## 枚举

枚举是最基础的构建类型的方法，你可以把 `Int32`， `Char8`， `Float32` 之类的类型都看作是通过枚举定义的。枚举元素使用关键词 `enum` 定义。一个简单的枚举类型可以这样表示：

```PlantUML
enum Color{
    Red
    Green
    Blue
}
```

其中 `Color` 是枚举类型名，花括号内的是枚举类型的所有可能取值。

## 类

类是面向对象中中最为核心的类型定义方式。一个面向对象的类往往是若干类型变量的集合。一般来说，这些变量会分为属性和方法两种。方法是函数型的类型的变量（或常量），方法则是非函数型的类型的变量（或常量）。

一个典型的类在 PlantUML 中是这样描述的：

```PlantUML
class Person{
    - age:int
    + name:string
    + Eat(food:Food)
    + Say() : string
}
```

`class` 是定义类的关键字， `Person` 是类名，花括号内是成员变量（或常量）列表。关于这个列表，有很多细节的东西需要介绍：

### 访问权限控制

每个成员定义的开头符号是访问权限控制符。对应面向对象设计中常用的四种权限， PlantUML 有四种符号分别是：

* `+` public
* `-` private
* `#` protected
* `~` package private

### 属性成员

属性成员除了访问权限控制，由变量名和变量类型两部分组成。变量名和类型名的先后顺序其实比较灵活。你可以像 C 那样先写类型名，空一格写变量名，也可以像 Python 类型标注那样先写变量名再写冒号，冒号后写类型名。不管选择哪种写法，统一就好，本教程中使用类型后置的写法，例如：

```PlantUML
+ name : string
```

如果有必要，你还可以用 `=` 给属性设置默认值，例如：

```PlantUML
+ name : string = "ZhiZe"
```

### 方法成员

方法成员的构成比属性成员复杂。一个方法成员除了访问控制，还由方法名、参数列表和返回值三个必要部分组成。方法名不必多说。参数列表是由圆括号括起来，逗号隔开的若干个参数。每个参数的写法都和属性的写法类似，由变量名和类型名组成。参数列表中的变量也可以加默认值，但是，一般来说有默认值的参数应当放到参数列表最后。

最后的返回值类型就是函数返回值的类型，它可以像写属性类型那样加冒号写到函数参数列表后边，也可以放 C 的语法写在函数名前边。

一些方法的例子如下：

```PlantUML
+ CalculateVolume(length : int, width : int = 5, height : int = 2) : int
```

### 抽象类和抽象方法

抽象类是只能被继承不能实例化的类，抽象方法是只有名称和原型定义没有实现的方法且只能存在于抽象类中。

在 PlantUML 中使用 `abstract` 替代 `class` 定义抽象类。在方法名前加 `{abstract}` 标签来定义抽象方法。在 UML 图中抽象类名和抽象方法都会以斜体书写。

```PlantUML
abstract Animal{
    + {abstract} Eat()
    + {abstract} Run()
}
```

### 静态成员

一般来说，类实例化后，每一个类实例都有自己的一套属性，而且每一个类实例的方法都只能访问自己的那一套属性，不能直接访问别的实例的属性。但你也可以设置一些属性或方法为静态，这些静态成员属于类本身而不属于任何具体的类实例。要标记静态成员可以使用 `{static}` 标签。在 UML 图中静态成员会有下划线，例如：

```PlantUML
class ComplexNumber{
    + real : float
    + imag : float
    + {static} pi : ComplexNumber
    + {static} Add(a : ComplexNumber, b : ComplexNumber) : ComplexNumber
}
```

### 其他成员标记

给成员使用的带花括号的标签其实是 UML 的一种拓展语法，一些在 UML 中没有约定特殊格式的修饰可以通过这种方式表示（它们会直接显示在函数名前）。

在此我们进行如下约定：

* `{const}` 表示编译时常量
* `{readonly}` 表示运行时只读变量
* `{virtual}` 表示虚拟方法
* `{override}` 表示重写方法

举个例子：

```PlantUML
class ComplexNumber{
    + real : float
    + imag : float
    + {const} pi : ComplexNumber
    + {override} Add(a : ComplexNumber, b : ComplexNumber) : ComplexNumber
}
```

## 接口

接口不是类，而是一种规定类必须实现的方法的协议。可以使用 `interface` 为关键词定义接口。接口的成员必须是函数，并且不标记访问权限（因为必须是 `public`）。类在实现接口的方法时也不需要标 `override`。

这里举个例子：

```PlantUML
interface ICountable{
    GetCount() : int
    AddOne() : int
}
```

## 成员分组

默认情况下 PlantUML 会将一个类的属性和方法分两组显示。你也可以自定义这种分组方法。

在定义类的花括号内使用 `..` 独占一行可以形成一条分界线。如果想要在这条分界线上加标注，就用一对 `..` 把标注文字括起来。例如：

```PlantUML
class User {
  .. Simple Getter ..
  + getName()
  + getAddress()
  .. Some setter ..
  + setName()
  .. private data ..
  int age
  .. encrypted ..
  String password
}
```

这个技巧也能用于枚举、接口之类由若干项目组成的节点图标。

```PlantUML
enum Char {
  A
  B
  C
  ..
  a
  b
  c
  ..
  1
  2
  3
  4
}
```

也可用别的符号替代 `..`，其他符号会形成不同的线性。目前可选的符号有：`--`， `__`， `==`。

## 泛型

泛型是一种批量生成代码的方法。在类 C 语言中往往使用 `<>` 来标记泛型。你可以把这种语法用到 PlantUML 中。例如：

```PlantUML
class A<T1, T2>{
    + {static} Method1<T>(x : T1, y : T) : T2
    + attribute1 : List<List<int>>
}
```

## 类标记

之前介绍过类成员可以用花括号括起来的成员标签修饰。对于类也有类似的机制。不过类的修饰符需要写在类名后边，并且用 `<<` 和 `>>` 括起来（注意和泛型类的语法区分）。例如：

```PlantUML
class A <<sealed>>{
    
}
```



@startuml
class A <<sealed>>{

}
@enduml