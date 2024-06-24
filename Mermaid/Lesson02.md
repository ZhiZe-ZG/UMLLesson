# 类节点

Class Diagram 图中节点以类节点为主。类节点由三个部分组成。其一是关键词 `class`，其二是类名，其三是花括号中的代码块。例如一个名为 `Animal` 的类可以表示为：

````markdown
```mermaid
classDiagram
    class Animal{
    }
```
````

渲染后的结果是

```mermaid
classDiagram
    class Animal{
    }
```

在类的花括号里可以填写类成员，每一行为一条类成员。类成员分为属性和方法两种。两种成员的语法不同， mermaid 会自动整理把属性和方法分为两部分显示。

属性由三个必选部分组成。第一部分是访问控制符号。共有四种符号可选：

* `+` 表示 public 访问权限
* `-` 表示 private 访问权限
* `#` 表示 protected 访问权限
* `~` 表示 internal (package 内部) 访问权限

第二部分则是冒号后的类型名。第三部分是属性名。

一些典型的属性可以表示为：

````markdown
```mermaid
classDiagram
    class Animal{
        +int age
        -string gender
    }
```
````

渲染后为：

```mermaid
classDiagram
    class Animal{
        +int age
        -string gender
    }
```

方法由四个必选部分组成。其一和属性一样是访问控制符。其二是方法名。其三是参数列表。参数列表要用括号括起来，其中不同的参数项由逗号分隔。第四个则是函数返回值类型。返回值类型写在参数列表之后，不需要冒号分隔，但是 mermaid 在渲染之后会给参数列表和返回值类型之间加冒号。

一个简单的无参数列表方法可以表示为：

```markdown
+IsMammal() bool
```

没有返回值的方法则可以不标注返回值类型，例如：

```markdown
+Eat(Food food)
```

非空的输入参数列表中每一项又由三部分组成——变量名、冒号和类型——这和属性的标注方法类似。例如：

```markdown
+Add(int x, int y) int
```

如果要为属性或者函数参数设置默认值，可以之间在变量名之后用 `=` 标识。

例如：

````markdown
```mermaid
classDiagram
    class Animal{
        +int age=10 
        -string gender 
        +SetAge(int x=0)
    }
```
````

渲染为：

```mermaid
classDiagram
    class Animal{
        +int age=10 
        -string gender 
        +SetAge(int x=0)
    }
```

对于函数参数来说，还有一类可选的标识。就是参数的输入输出类型。一般来说函数的参数都是输入类型的。也就是说调用函数时的实参可以赋值给形参，但是形参的值改变不能反过来改变实参。但为了编程方便，很多语言打破了纯函数式的要求，允许形参影响实参。因而有三种输入输出类型——只输入的 `in`（不加输入输出类型标识的变量默认是 `in` 类型），只输出的 `out`（形参反向影响实参），可以输入输出的 `inout`。

这里举一个例子：

```markdown
+Divide(in int dividend, in int divisor, out int remainder) int 
```

对于类属性和类方法，还有一个通用的修饰——静态修饰。静态的属性和方法并不属于类的实例而是属于类本身，可以通过类名直接访问并由所属类的所有类实例共享。 mermaid 本身支持使用 `$` 表示静态修饰，并将其修饰为带下划线的形式。对于属性来说， `$` 放置于其变量名之后，对于方法来说， `$` 放置在参数列表括号之后。例如：

````markdown
```mermaid
classDiagram
    class Complex{
        +float real 
        +float imag 
        +float pi$
        +Add(x : Complex, y : Complex)$ Complex
    }
```
````

渲染后为：

```mermaid
classDiagram
    class Complex{
        +float real 
        +float imag 
        +float pi$
        +Add(x : Complex, y : Complex)$ Complex
    }
```
