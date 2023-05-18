# Kivy 基础

Kivy 依赖于许多库，例如 SDL2、gstreamer、PIL、Cairo 等。它们并非都是必需的，但根据您正在使用的平台，安装它们可能会很麻烦。为了简化您的开发过程，我们为 Windows、macOS 和 Linux 提供预打包的二进制文件。

请查看以下页面之一以获取详细的安装说明：

* [在 Windows 上安装](https://kivy.org/doc/stable/installation/installation-windows.html#installation-windows)
* [在 macOS 上安装](https://kivy.org/doc/stable/installation/installation-osx.html#installation-osx)
* [在 Linux 上安装](https://kivy.org/doc/stable/installation/installation-linux.html#installation-linux)
* [在树莓派上安装](https://kivy.org/doc/stable/installation/installation-rpi.html#installation-rpi)

或者，可以在此处找到开发版本的说明：

* [开发安装](https://kivy.org/doc/stable/gettingstarted/installation.html#kivy-dev-install)

### 创建一个应用程序[¶](https://kivy.org/doc/stable/guide/basic.html#create-an-application)

创建一个 kivy 应用程序非常简单：

* 继承[`App`](https://kivy.org/doc/stable/api-kivy.app.html#kivy.app.App)
* 实现它的[`build()`](https://kivy.org/doc/stable/api-kivy.app.html#kivy.app.App.build)方法所以它返回一个 `Widget`实例（你的小部件树的根）
* 实例化这个类，并调用它的[`run()`](https://kivy.org/doc/stable/api-kivy.app.html#kivy.app.App.run) 方法。

这是一个最小应用程序的示例：

```
import kivy
kivy.require('2.1.0') # replace with your current kivy version !

from kivy.app import App
from kivy.uix.label import Label


class MyApp(App):

    def build(self):
        return Label(text='Hello world')


if __name__ == '__main__':
    MyApp().run()
```

您可以将其保存到一个文本文件中，例如_main.py ，然后运行它。_

### Kivy 应用生命周期[¶](https://kivy.org/doc/stable/guide/basic.html#kivy-app-life-cycle)

首先，让我们熟悉一下 Kivy 应用程序的生命周期。

<figure><img src="https://kivy.org/doc/stable/_images/Kivy_App_Life_Cycle.png" alt=""><figcaption><p>kivy应用的生命周期</p></figcaption></figure>

正如您在上面看到的，出于所有意图和目的，我们应用程序的入口点是 run() 方法，在我们的例子中是“MyApp().run()”。我们将回到这一点，但让我们从这行开始：

```
from kivy.app import App
```

要求您的 App 的基类继承自_App_类。它存在于 kivy\_installation\_dir/kivy/app.py 中。

笔记

如果您想更深入地研究 Kivy App 类的功能，请继续打开该文件。我们鼓励您打开代码并通读它。Kivy基于Python，使用Sphinx[^1]做文档，所以每个类的文档都在实际文件中。

同样在第 5 行：

```
from kivy.uix.label import Label
```

这里要注意的一件重要事情是包/类的布局方式。该 [`uix`](https://kivy.org/doc/stable/api-kivy.uix.html#module-kivy.uix)模块是包含用户界面元素（如布局和小部件）的部分。

继续第 8 行：

```
class MyApp(App):
```

这是我们_定义_Kivy 应用程序基类的地方。_您应该只需要在此行中更改您的应用程序MyApp_的名称。

继续第 10 行：

```
def build(self):
```

如上图突出显示，显示了_Kivy App Life Cycle 的外壳，这是您应该初始化并返回Root Widget 的_函数。这是我们在第 11 行所做的：

```
return Label(text='Hello world')
```

这里我们用文本“Hello World”初始化一个标签并返回它的实例。此标签将成为此应用程序的根小部件。

笔记

Python 使用缩进来表示代码块，因此请注意，在上面提供的代码中，类和函数定义在第 11 行结束。

现在让我们的应用程序在第 14 行和第 15 行运行：

```
if __name__ == '__main__':
    MyApp().run()
```

这里初始化了类_MyApp并调用了它的 run() 方法。_这将初始化并启动我们的 Kivy 应用程序。

### 运行应用程序[¶](https://kivy.org/doc/stable/guide/basic.html#running-the-application)

要运行该应用程序，请按照适用于您的操作系统的说明进行操作：

适用于 Windows、Linux、macOS 或 RPi。从你安装 Kivy 的[终端](https://kivy.org/doc/stable/gettingstarted/installation.html#command-line) 运行：

```
python main.py
```

对于 Android 或 iOS，您的应用程序需要一些补充文件才能运行。请参阅[创建适用于 Android 的程序包](https://kivy.org/doc/stable/guide/packaging-android.html)或参阅[创建适用于 iOS 的程序包](https://kivy.org/doc/stable/guide/packaging-ios.html)以供进一步参考。

应打开一个窗口，显示覆盖整个窗口区域的单个标签（带有文本“Hello World”）。这里的所有都是它的。

![../\_images/quickstart.png](https://kivy.org/doc/stable/\_images/quickstart.png)

### 自定义应用程序[¶](https://kivy.org/doc/stable/guide/basic.html#customize-the-application)

让我们稍微扩展一下这个应用程序，比如说一个简单的用户名/密码页面。

```
from kivy.app import App
from kivy.uix.gridlayout import GridLayout
from kivy.uix.label import Label
from kivy.uix.textinput import TextInput


class LoginScreen(GridLayout):

    def __init__(self, **kwargs):
        super(LoginScreen, self).__init__(**kwargs)
        self.cols = 2
        self.add_widget(Label(text='User Name'))
        self.username = TextInput(multiline=False)
        self.add_widget(self.username)
        self.add_widget(Label(text='password'))
        self.password = TextInput(password=True, multiline=False)
        self.add_widget(self.password)


class MyApp(App):

    def build(self):
        return LoginScreen()


if __name__ == '__main__':
    MyApp().run()
```

在第 2 行，我们导入一个`Gridlayout`：

```
from kivy.uix.gridlayout import GridLayout
```

此类用作我们在第 7 行定义的根小部件 (LoginScreen) 的基础：

```
class LoginScreen(GridLayout):
```

在类 LoginScreen 的第 9 行，我们覆盖了该方法 `__init__()`以添加小部件并定义它们的行为：

```
def __init__(self, **kwargs):
    super(LoginScreen, self).__init__(**kwargs)
```

人们不应该忘记调用 super 以实现被重载的原始类的功能。_另请注意，在调用 super 时不要省略\*\*kwargs_是一个好习惯，因为它们有时会在内部使用。

继续前往 11 号线及以后：

```
self.cols = 2
self.add_widget(Label(text='User Name'))
self.username = TextInput(multiline=False)
self.add_widget(self.username)
self.add_widget(Label(text='password'))
self.password = TextInput(password=True, multiline=False)
self.add_widget(self.password)
```

我们要求 GridLayout 在两列中管理其子项，并 为用户名和密码添加一个[`Label`](https://kivy.org/doc/stable/api-kivy.uix.label.html#kivy.uix.label.Label)和一个。[`TextInput`](https://kivy.org/doc/stable/api-kivy.uix.textinput.html#kivy.uix.textinput.TextInput)

运行上面的代码会给你一个应该看起来像这样的窗口：

![../\_images/guide\_customize\_step1.png](https://kivy.org/doc/stable/\_images/guide\_customize\_step1.png)

尝试重新调整窗口大小，您将看到屏幕上的小部件根据窗口大小自行调整，您无需执行任何操作。这是因为小部件默认使用大小提示。

上面的代码不处理用户的输入，不进行验证或其他任何操作。`Widget` 我们将在接下来的部分中更深入地研究这一点以及规模和定位。

[^1]: 
