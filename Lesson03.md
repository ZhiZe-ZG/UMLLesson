# 抽象类和接口

在一般的面向对象程序设计模式中，并非所有的类都是普通类。例如为了方便继承和重载，许多面向对象编程语言中会有抽象类、抽象方法和接口等语法。

抽象类在 mermaid 中没有专门的关键词，而是通过在普通类花括号内第一行加 `<<abstract>>` 表示。一个抽象的 `Animal` 类可以记为：

````
```mermaid
classDiagram
    class Animal{
        <<abstract>>
    }
    
```
````

渲染为：

```mermaid
classDiagram
    class Animal{
        <<abstract>>
    }
    
```

抽象方法则通过在函数参数列表括号后边加 `*` 来表示。 mermaid 可以将抽象方法自动渲染为斜体。例如：

````
```mermaid
classDiagram
    class Animal{
        <<abstract>>
        +GetAge() * int
    }
    
```
````

渲染为：

```mermaid
classDiagram
    class Animal{
        <<abstract>>
        +GetAge() * int
    }
    
```

遗憾的是，对同样影响基础与重载关系的关键词 `virtual` 和 `override`， mermaid 没有专门的语法规则。我们可以约定以 `^` 加在方法名前来表示方法是虚方法，用 `@` 加在方法名前表示重载方法。例如：

```mermaid
classDiagram
    class Animal{
        +^Eat()
    }
    class Dog{
        +@Eat()
    }
    Animal <|-- Dog  
```

> 不过如果你不需要表现方法之间的重写关系，可以不使用这一套记号。

类之间的多重继承往往会导致方法实现的混乱。为了解决这个问题一些语言引入了接口机制。接口不是类，但可以被类继承，而且一个类可以继承多个接口。并且，接口的成员只有方法而没有属性。这些接口必须在继承了接口的类型中以 `public` 的方式实现。不过由于接口并不是类，当一个类实现了接口的方法，无需使用 `override` 修饰。

接口类则可以通过加 `<<interface>>` 表示，接口中的方法则都不需要访问控制标记。例如：

````
```mermaid
classDiagram
    class IComparable{
        <<interface>>
        Bigger() bool
        Smaller() bool
    }
    
```
````

渲染为：

```mermaid
classDiagram
    class IComparable{
        <<interface>>
        Bigger() bool
        Smaller() bool
    }
    
```
