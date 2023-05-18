# 配置 Kivy

kivy 的配置文件名为_config.ini_，并遵循[标准的 INI](http://en.wikipedia.org/wiki/INI\_file)格式。

### 确定配置文件的位置[¶](https://kivy.org/doc/stable/guide/config.html#locating-the-configuration-file)

配置文件的位置由环境变量_KIVY\_HOME配置_：

```
<KIVY_HOME>/config.ini
```

在桌面上，这默认为：

```
<HOME_DIRECTORY>/.kivy/config.ini
```

因此，如果您的用户名为“tito”，则该文件将位于：

* Windows：`C:\Users\tito\.kivy\config.ini`
* macOS：`/Users/tito/.kivy/config.ini`
* Linux：`/home/tito/.kivy/config.ini`

在 Android 上，这默认为：

```
<ANDROID_APP_PATH>/.kivy/config.ini
```

如果您的应用名为“org.kivy.launcher”，则该文件将在此处：

```
/data/data/org.kivy.launcher/files/.kivy/config.ini
```

在 iOS 上，这默认为：

```
<HOME_DIRECTORY>/Documents/.kivy/config.ini
```

### 本地配置[¶](https://kivy.org/doc/stable/guide/config.html#local-configuration)

有时只希望更改某些应用程序的配置，或者在测试 Kivy 的单独部分（例如输入提供程序）期间更改配置。要创建一个单独的配置文件，您可以简单地使用这些命令：

```
from kivy.config import Config

Config.read(<file>)
# set config
Config.write()
```

当单个文件的本地配置`.ini`不够时，例如，当你想为_garden_、 kivy 日志和其他东西拥有单独的环境时，你需要更改`KIVY_HOME`应用程序中的环境变量以获得所需的结果：

```
import os
os.environ['KIVY_HOME'] = <folder>
```

或者在每次运行应用程序之前在控制台中手动更改它：

1.  Windows：

    ```
    set KIVY_HOME=<folder>
    ```
2.  Linux & OSX：

    ```
    export KIVY_HOME=<folder>
    ```

更改后，该文件夹的行为将与上述`KIVY_HOME`默认文件夹完全相同。`.kivy/`

### 了解配置令牌[¶](https://kivy.org/doc/stable/guide/config.html#understanding-config-tokens)

所有配置令牌都在[`kivy.config`](https://kivy.org/doc/stable/api-kivy.config.html#module-kivy.config) 模块中进行了说明。
