# kv设计语言

Kivy 提供了一种专门针对简单和可扩展的 GUI 的设计语言。该语言使界面设计与应用程序逻辑分离变得简单，遵循 关注点分离原则。例如：

```python
// 你的应用程序中的每一个类都可以由kv文件中这样的规则来表示
<LoginScreen>
    f_username: username
    f_password: password
    // 这就是你如何将你的widget/layout添加到父类中的方法 (注意缩进)。
    GridLayout:
        // 这是你如何设置你的widget/layout的每个属性的方法
        rows: 2
        cols: 2
        padding: 10
        spacing: 10
        Label:
            text: 'User Name'
        TextInput:
            id: username
        Label:
            text: 'Password'
        TextInput:
            id: password
            password: True
```
