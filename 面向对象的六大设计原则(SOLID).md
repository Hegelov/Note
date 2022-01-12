# 面向对象的六大设计原则(SOLID)

#### 一、SOLID

**设计模式的六大原则有：**

- Single Responsibility Principle：单一职责原则
- Open Closed Principle：开闭原则
- Liskov Substitution Principle：里氏替换原则
- Law of Demeter：迪米特法则
- Interface Segregation Principle：接口隔离原则
- Dependence Inversion Principle：依赖倒置原则

把这六个原则的首字母联合起来（两个 L 算做一个）就是 SOLID （solid，稳定的），其代表的含义就是这六个原则结合使用的好处：建立稳定、灵活、健壮的设计。

#### 二、单一职责原则（Single Responsibility Principle）

一个类应该只有一个发生变化的原因

> There should never be more than one reason for a class to change.

单一职责原则简称 SRP ，顾名思义，就是一个类只负责一个职责。那这个原则有什么用呢，它让类的职责更单一。这样的话，每个类只需要负责自己的那部分，类的复杂度就会降低。如果职责划分得很清楚，那么代码维护起来也更加容易。试想如果所有的功能都放在了一个类中，那么这个类就会变得非常臃肿，而且一旦出现bug，要在所有代码中去寻找；更改某一个地方，可能要改变整个代码的结构，想想都非常可怕。当然一般时候，没有人会去这么写的。

当然，这个原则不仅仅适用于类，对于接口和方法也适用，即一个接口/方法，只负责一件事，这样的话，接口就会变得简单，方法中的代码也会更少，易读，便于维护。

事实上，由于一些其他的因素影响，类的单一职责在项目中是很难保证的。通常，接口和方法的单一职责更容易实现。

##### 单一职责原则的好处

- 代码的粒度降低了，类的复杂度降低了。

- 可读性提高了，每个类的职责都很明确，可读性自然更好。

- 可维护性提高了，可读性提高了，一旦出现 bug ，自然更容易找到他问题所在。

- 改动代码所消耗的资源降低了，更改的风险也降低了。

  

#### 三、开闭原则（Open Closed Principle）

一个软件实体，如类、模块和函数应该对扩展开放，对修改关闭

> Software entities like classes, modules and functions should be open for extension but closed for modification



#### 四、里氏替换原则（Liskov Substitution Principle）

所有引用基类的地方必须能透明地使用其子类的对象

> Functions that use use pointers or references to base classes must be able to use objects of derived classes without knowing it.



#### 五、迪米特法则（Law of Demeter）

只与你的直接朋友交谈，不跟“陌生人”说话

> Talk only to your immediate friends and not to strangers

其含义是：如果两个软件实体无须直接通信，那么就不应当发生直接的相互调用，可以通过第三方转发该调用。其目的是降低类之间的耦合度，提高模块的相对独立性。



#### 六、接口隔离原则（Interface Segregation Principle）

1、客户端不应该依赖它不需要的接口。
 2、类间的依赖关系应该建立在最小的接口上。

> Clients should not be forced to depend upon interfaces that they don`t use.
>  The dependency of one class to another one should depend on the smallest possible.

注：该原则中的接口，是一个泛泛而言的接口，不仅仅指Java中的接口，还包括其中的抽象类。



#### 七、依赖倒置原则（Dependence Inversion Principle）

1、上层模块不应该依赖底层模块，它们都应该依赖于抽象。
 2、抽象不应该依赖于细节，细节应该依赖于抽象。

> High level modules should not depend upon low level modules. Both should depend upon abstractions.
>  Abstractions should not depend upon details. Details should depend upon abstractions.



