# 类型关系的表示

## 继承和实现

类之间的继承关系需要额外的类关系说明语句定义。类之间的继承关系使用 `<|--` 链接两个类名表示，箭头一侧是父类，箭尾一侧是子类。

类和接口之间则有实现关系。实现关系用 `<|..` 表示，箭头一侧是接口，箭尾一侧是类。例如：

```PlantUML
interface ICanMove{}

class Animal{

}

class Dog{

}

class Cat{

}

Animal <|-- Dog
Animal <|-- Cat
ICanMove <|.. Animal
```

渲染后 `<|--` 和 `<|..` 都使用空心大箭头，不过 `<|--` 是实线， `<|..` 是虚线。

## 依赖关系

@startuml
interface ICanMove{}

class Animal{

}

class Dog{

}

class Cat{

}

Animal <|-- Dog
Animal <|-- Cat
ICanMove <|.. Animal
@enduml

