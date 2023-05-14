# 事件

Kivy 主要是[基于事件的](http://en.wikipedia.org/wiki/Event-driven\_programming)，这意味着程序的流程由事件决定。

**时钟事件**

![../\_images/gs-events-clock.png](https://kivy.org/doc/stable/\_images/gs-events-clock.png)

时钟对象(clock object)允许你使用`schedule_once()`方法在未来安排一次性事件的函数调用，或使用`schedule_interval()`方法安排重复事件的函数调用。

您还可以使用 `create_trigger()`方法创建触发事件。触发器的优点是每帧只调用一次，即使您为相同的回调安排了多个触发器。

**输入事件**

![../\_images/gs-events-input.png](https://kivy.org/doc/stable/\_images/gs-events-input.png)

所有鼠标单击、触摸和滚轮事件都是`MotionEvent`的一部分，通过输入后处理（Input Postprocessing）扩展，并通过`Window`类中的`on_motion`事件调度。然后此事件在小部件`Widget`中生成 `on_touch_down()`, `on_touch_move()`和 `on_touch_up()`事件。

如果要深入理解，请查看输入管理。

**类事件(class events)**

![../\_images/gs-events-class.png](https://kivy.org/doc/stable/\_images/gs-events-class.png)

我们的基类`EventDispatcher`由`Widget`调用，根据我们的属性(Properties)更改。这意味着当一个`Widget`改变它的位置或大小时，相应的事件会自动触发。

此外，你可以使用`register_event_type()`方法创建自己的事件，就像`Button`小部件中的`on_press`和`on_release`事件一样。

另一个需要注意的是，如果你重写一个事件，你就需要负责实现基类之前处理的所有行为。最简单的方法是调用`super()`：

```
def on_touch_down(self, touch):
    if super().on_touch_down(touch):
        return True
    if not self.collide_point(touch.x, touch.y):
        return False
    print('you touched me!')
    return True
```

通过阅读事件和属性文档来熟悉事件。
