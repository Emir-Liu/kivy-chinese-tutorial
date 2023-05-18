# 控制环境

许多环境变量可用于控制 Kivy 的初始化和行为。

例如，为了将文本呈现限制为 PIL 实现：

```
$ KIVY_TEXT=pil python main.py
```

在导入kivy之前应该设置环境变量：

```
import os
os.environ['KIVY_TEXT'] = 'pil'
import kivy
```

### 路径控制[¶](https://kivy.org/doc/stable/guide/environment.html#path-control)

新版本 1.0.7。

您可以控制配置文件、模块和 kivy 数据所在的默认目录。

KIVY\_DATA\_DIR

Kivy 数据的位置，默认为_\<kivy path>/data_

KIVY\_MODULES\_DIR

Kivy 模块的位置，默认为_\<kivy path>/modules_

KIVY\_HOME

Kivy根目录的位置。该目录用于本地配置，必须位于可写位置。

默认为：

* 桌面：_<用户主目录>/.kivy_
* 安卓：_<安卓应用路径>/.kivy_
* iOS：_<用户主页>/Documents/.kivy_

新版本 1.9.0。

KIVY\_SDL2\_PATH

如果设置，则在编译 kivy 时将使用此路径中的 SDL2 库和标头，而不是系统范围内安装的库和标头。要在运行 kivy 应用程序时使用相同的库，必须将此路径添加到 PATH 环境变量的开头。

新版本 1.9.0。

警告

Kivy 的编译需要这个路径。程序执行不需要它。

### 配置[¶](https://kivy.org/doc/stable/guide/environment.html#configuration)

KIVY\_USE\_DEFAULTCONFIG

如果在 environ 中找到这个名字，Kivy 将不会读取用户配置文件。

KIVY\_NO\_CONFIG

如果设置，则不会读取或写入任何配置文件。这也适用于用户配置目录。

KIVY\_NO\_FILELOG

如果设置，日志将不会打印到文件

KIVY\_NO\_CONSOLELOG

如果设置，日志将不会打印到控制台

KIVY\_NO\_ARGS

如果设置为 ('true', '1', 'yes') 之一，命令行中传递的参数将不会被 Kivy 解析和使用。也就是说，您可以使用自己的参数安全地制作脚本或应用程序，而无需_-_分隔符：

```
import os
os.environ["KIVY_NO_ARGS"] = "1"
import kivy
```

新版本 1.9.0。

KCFG\_section\_key

如果检测到这样的格式环境名称，它将被映射到 Config 对象。当导入_kivy_时，它们只加载一次。_可以使用KIVY\_NO\_ENV\_CONFIG_禁用该行为。

```
import os
os.environ["KCFG_KIVY_LOG_LEVEL"] = "warning"
import kivy
# during import it will map it to:
# Config.set("kivy", "log_level", "warning")
```

新版本 1.11.0。

KIVY\_NO\_ENV\_CONFIG

如果设置，则没有环境密钥将映射到配置对象。如果未设置，任何_KCFG\_section\_key=value_都将映射到 Config。

新版本 1.11.0。&#x20;

### 将核心限制在特定的实现上[¶](https://kivy.org/doc/stable/guide/environment.html#restrict-core-to-specific-implementation)

[`kivy.core`](https://kivy.org/doc/stable/api-kivy.core.html#module-kivy.core)尝试选择适用于您的平台的最佳实现。对于测试或自定义安装，您可能希望将选择器限制为特定的实现。

KIVY\_WINDOW 窗口

用于创建窗口的实现

值：sdl2、pygame、x11、egl\_rpi

KIVY\_TEXT

用于渲染文本的实现

值：sdl2、pil、pygame、sdlttf

KIVY\_VIDEAO

用于渲染视频的实现

值：gstplayer、ffpyplayer、ffmpeg、null

KIVY\_AUDIO

用于播放音频的实现

值：sdl2、gstplayer、ffpyplayer、pygame、avplayer

KIVY\_IMAGE

用于读取图像的实现

值：sdl2、pil、pygame、imageio、tex、dds

在版本 2.0.0 中更改。

删除了 GPL _gif_实现

KIVY\_CAMERA

用于读取相机的实现

值：avfoundation、android、opencv

KIVY\_SPELLING

用于拼写的实现

值：附魔，osxappkit

KIVY\_CLIPBOARD

用于剪贴板管理的实现

值：sdl2、pygame、dummy、android

### 指标[¶](https://kivy.org/doc/stable/guide/environment.html#metrics)

KIVY\_DPI

如果设置，该值将用于`Metrics.dpi`。

版本 1.4.0 的新内容

KIVY\_METRICS\_DENSITY

如果设置，该值将用于`Metrics.density`。

版本 1.5.0 的新内容

KIVY\_METRICS\_FONTSCALE

> 如果设置，该值将用于`Metrics.fontscale`。
>
> 在版本 1.5.0 中出现

### 图形[¶](https://kivy.org/doc/stable/guide/environment.html#graphics)

KIVY\_GL\_BACKEND

要使用的 OpenGL 后端。看[`cgl`](https://kivy.org/doc/stable/api-kivy.graphics.cgl.html#module-kivy.graphics.cgl)。

KIVY\_GL\_DEBUG

是否记录 OpenGL 调用。看[`cgl`](https://kivy.org/doc/stable/api-kivy.graphics.cgl.html#module-kivy.graphics.cgl)。

KIVY\_GRAPHICS

是否使用 OpenGL ES2。看[`cgl`](https://kivy.org/doc/stable/api-kivy.graphics.cgl.html#module-kivy.graphics.cgl)。

KIVY\_GLES\_LIMITS

是否强制执行 GLES2 限制（默认值，或者如果设置为 1）。如果设置为 false，Kivy 将不会真正兼容 GLES2。

以下是设置为 true 时导致的潜在不兼容性列表。

| 网格索引 | 如果为真，则网格中的索引数限制为 65535                                                                                                                                                               |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 纹理块  | 当 blitting 到纹理时，数据（颜色和缓冲区）格式必须与纹理创建时使用的格式相同。在桌面上，不同颜色的转换由驱动程序正确处理，而在 Android 上，大多数设备无法做到这一点。参考：https: [//github.com/kivy/kivy/issues/1600](https://github.com/kivy/kivy/issues/1600) |

> 版本 1.8.1 的新内容

KIVY\_BCM\_DISPMANX\_ID

更改要使用的默认 Raspberry Pi 显示。可用值列表可在_vc\_dispmanx\_types.h_中访问。默认值为 0：

* 0：DISPMANX\_ID\_MAIN\_LCD
* 1：DISPMANIX\_ID\_AUX\_LCD
* 2：DISPMANIX\_ID\_HDMI
* 3：DISPMANIX\_ID\_SDTV
* 4：DISPMANX\_ID\_FORCE\_LCD
* 5：DISPMANIX\_ID\_FORCE\_TV
* 6：DISPMANIX\_ID\_FORCE\_OTHER

KIVY\_BCM\_DISPMANIX\_LAYER

更改默认的 Raspberry Pi dispmanx 层。默认值为 0。

版本 1.10.1 的新内容

### 事件循环[¶](https://kivy.org/doc/stable/guide/environment.html#event-loop)

KIVY\_EVENTLOOP

当应用程序以异步方式运行时，应使用哪个异步库。请参阅[`kivy.app`](https://kivy.org/doc/stable/api-kivy.app.html#module-kivy.app)示例用法。

`'asyncio'`：当应用程序以异步方式并使用标准 library asyncio 包时。如果未设置，则它为默认值。

`'trio'`：当应用程序以异步方式运行并且使用包`trio`

版本 2.0.0 的新内容
