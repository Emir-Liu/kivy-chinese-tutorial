# 属性

kivy引入了一种在类中声明属性的新方法。

之前在类中声明属性的代码如下：

```
class MyClass(object):
    def __init__(self):
        super(MyClass,self).__init__()
        self.numeric_var = 1
```

使用kivy属性后，代码如下：

```
class MyClass(EventDispatcher):
    numeric_var = NumericProperty(1)
```

这些属性使用了观察者模式(observer pattern)，它们有下面的好处：

* 容易操作用Kv语言定义的小部件(widgets)
* 自动发现任何变动并且调用对应的函数或者代码
* 检查和验证数值
* 优化内存管理

使用这个方法，你需要在类中声明。即直接在类中，而不是在类的方法中。

属性将自动建立实例的类属性。

所有的属性默认提供一个`on_<propertyname>`事件，当属性的状态或者值改变的时候就会调用。

kivy提供以下的属性：

`NumericProperty`, `StringProperty`, `ListProperty`, `ObjectProperty`, `BooleanProperty`, `BoundedNumericProperty`, `OptionProperty`, `ReferenceListProperty`, `AliasProperty`, `DictProperty`, `VariableListProperty`, `ConfigParserProperty`, `ColorProperty`

更加详细的介绍，在xx中。
