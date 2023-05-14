# kivy安装

Kivy 2.1.0 正式支持 Python **3.7-3.10**版本。

| ‎                                                                                                                                                | Platform | Installation       | Packaging             |
| ------------------------------------------------------------------------------------------------------------------------------------------------ | -------- | ------------------ | --------------------- |
| [![w\_logo](https://kivy.org/doc/stable/\_images/windows.png)](https://kivy.org/doc/stable/\_images/windows.png)                                 | Windows  | pip                | PyInstaller           |
| [![m\_logo](https://kivy.org/doc/stable/\_images/macosx.png)](https://kivy.org/doc/stable/\_images/macosx.png)                                   | macOS    | pip, Kivy.app      | Kivy.app, PyInstaller |
| [![l\_logo](https://kivy.org/doc/stable/\_images/linux.png)](https://kivy.org/doc/stable/\_images/linux.png)                                     | Linux    | pip, PPA           | —                     |
| [![r\_logo](https://kivy.org/doc/stable/\_images/raspberrypi.png)](https://kivy.org/doc/stable/\_images/raspberrypi.png)                         | RPi      | pip                | —                     |
| [![a\_logo](https://kivy.org/doc/stable/\_images/android.png)](https://kivy.org/doc/stable/\_images/android.png)                                 | Android  | python-for-android | python-for-android    |
| [![i\_logo](https://kivy.org/doc/stable/\_images/IOS\_wordmark\_\(2017\).svg)](https://kivy.org/doc/stable/\_images/IOS\_wordmark\_\(2017\).svg) | iOS      | kivy-ios           | kivy-ios              |
| [![c\_logo](https://kivy.org/doc/stable/\_images/conda.png)](https://kivy.org/doc/stable/\_images/conda.png)                                     | Anaconda | conda              | —                     |

### 使用 pip&#x20;

安装 Kivy 的最简单方法是使用`pip`，它使用 [预编译的轮子](https://kivy.org/doc/stable/gettingstarted/installation.html#pip-wheel)（如果可用）安装 Kivy，否则使用源代码（见下文）。

Kivy为 Windows、macOS、Linux 和 RPi 上支持的 Python 版本提供了[预编译的轮子。](https://kivy.org/doc/stable/gettingstarted/installation.html#kivy-wheel-install)或者， 对于上面未列出的较新的 Python 版本，或者如果轮子不工作或无法正常运行，则需要[从源安装。](https://kivy.org/doc/stable/gettingstarted/installation.html#kivy-source-install)

#### 设置终端和 pip&#x20;

在安装 Kivy 之前，需要[预先安装](https://kivy.org/doc/stable/gettingstarted/installation.html#install-python)Python 和 pip 。然后，启动一个有 [Python 可用的](https://kivy.org/doc/stable/gettingstarted/installation.html#install-python)[新终端](https://kivy.org/doc/stable/gettingstarted/installation.html#command-line)。在终端中，更新和其他安装依赖项，以便您拥有最新版本，如下所示（对于 linux 用户，您可能必须替换而不是并在虚拟环境之外的后续命令中添加标志）：`pippython3python--user`

```
python -m pip install --upgrade pip setuptools virtualenv
```

#### 创建虚拟环境

为您的 Kivy 项目创建一个新的[虚拟环境](https://virtualenv.pypa.io/en/latest/) 。虚拟环境将防止可能与其他 Python 版本和包发生安装冲突。它是可选的**，但强烈推荐**：

1.  `kivy_venv`创建在当前目录中命名的虚拟环境：

    ```
    python -m virtualenv kivy_venv
    ```
2.  激活虚拟环境。**每次**启动新终端时，您都必须从当前目录执行此步骤 。这会设置环境，以便`kivy_venv` 使用新的 Python。

    对于**Windows 默认 CMD**，在命令行中执行：

    ```
    kivy_venv\Scripts\activate
    ```

    **如果您在Windows**上的 bash 终端中，请执行以下操作：

    ```
    source kivy_venv/Scripts/activate
    ```

    如果您使用的是**linux**或**macOS**，请执行以下操作：

    ```
    source kivy_venv/bin/activate
    ```

您的终端现在应该在路径前加上类似 的内容`(kivy_venv)`，表示`kivy_venv`环境处于活动状态。如果它不这样说，则虚拟环境不活动，以下将不起作用。

#### 安装 Kivy

最后，使用以下选项之一安装 Kivy：

**预编译的轮子**

最简单的是安装当前稳定版本的 PyPi wheels `kivy`，也可以选择`kivy_examples` 从 kivy-team 提供的 PyPi wheels 安装。简单地做：

```
python -m pip install "kivy[base]" kivy_examples
```

这也会安装 Kivy 的最小依赖项。要额外安装 支持**音频/视频**的 Kivy ，请安装`kivy[base,media]`或`kivy[full]`. 请参阅Kivy 的依赖项以获取选择器列表。

对于树莓派， 在安装上面的 Kivy 之前，你必须额外安装[源依赖项中列出的依赖项。](https://kivy.org/doc/stable/installation/installation-rpi.html#install-source-rpi)

**来自源头**

如果轮子不可用或不工作，可以通过一些额外的步骤从源代码安装 Kivy。从源代码安装意味着 Kivy 将从源代码安装并直接在您的系统上编译。

首先安装为每个平台列出的附加系统依赖项： [Windows](https://kivy.org/doc/stable/installation/installation-windows.html#install-source-win)、[macOS](https://kivy.org/doc/stable/installation/installation-osx.html#install-source-osx)、 [Linux](https://kivy.org/doc/stable/installation/installation-linux.html#install-source-linux)、[RPi](https://kivy.org/doc/stable/installation/installation-rpi.html#install-source-rpi)。

安装依赖项后，您现在可以将 Kivy 安装到虚拟环境中。

要安装稳定版的 Kivy，从终端执行：

```
python -m pip install "kivy[base]" kivy_examples --no-binary kivy
```

**要从master**安装最新的尖端 Kivy ，请执行以下操作：

```
python -m pip install "kivy[base] @ https://github.com/kivy/kivy/archive/master.zip"
```

如果你想从不同的分支安装 Kivy，从你的分支存储库，或者从一个特定的提交（例如测试来自用户的 PR 的修复）替换 url 的相应组件。

例如从`stable`分支安装，url 变为 `https://github.com/kivy/kivy/archive/stable.zip`. 或者尝试特定的提交哈希，使用例如 `https://github.com/kivy/kivy/archive/3d3e45dda146fef3f4758aea548da199e10eb382.zip`

**预发布、预编译的轮子**

要安装 Kivy 的最后一个**预发布**版本的预编译轮，而不是当前的稳定版本，请将`--pre`标志添加到 pip：

```
python -m pip install --pre "kivy[base]" kivy_examples
```

[如果 Kivy 已发布到PyPi](https://pypi.org/project/Kivy/#history)，这将只安装开发版本 。相反，您还可以通过以下方式从 Kivy 服务器安装最新的**尖端** Nightly wheels ：

```
python -m pip install kivy --pre --no-deps --index-url  https://kivy.org/downloads/simple/
python -m pip install "kivy[base]" --pre --extra-index-url https://kivy.org/downloads/simple/
```

它分两步完成，否则`pip`可能会忽略服务器上的轮子并从 PyPi 安装较旧的预发布版本。

对于树莓派，记得 在安装上面的 Kivy 之前额外安装[源依赖项中列出的依赖项。](https://kivy.org/doc/stable/installation/installation-rpi.html#install-source-rpi)

**开发安装**

如果你想在安装 Kivy 之前编辑它，或者如果你想尝试修复一些 Kivy 问题并提交包含修复的拉取请求，你需要先下载 Kivy 源代码。以下步骤假定 git 已预安装并在终端中可用。

典型的过程是在本地克隆 Kivy：

```
git clone git://github.com/kivy/kivy.git
```

这会在您当前的路径中创建一个名为 kivy 的文件夹。接下来，安装为每个操作系统列出的附加系统依赖项：[Windows](https://kivy.org/doc/stable/installation/installation-windows.html#install-source-win)、 [macOS](https://kivy.org/doc/stable/installation/installation-osx.html#install-source-osx)、[Linux](https://kivy.org/doc/stable/installation/installation-linux.html#install-source-linux)、 [RPi](https://kivy.org/doc/stable/installation/installation-rpi.html#install-source-rpi)。

然后切换到 kivy 目录并将 Kivy 安装为 [可编辑安装](https://pip.pypa.io/en/stable/cli/pip\_install/#editable-installs)：

```
cd kivy
python -m pip install -e ".[dev,full]"
```

现在，您可以使用 git 更改分支、编辑代码并提交 PR。每次更改 cython 文件时，请记住编译 Kivy，如下所示：

```
python setup.py build_ext --inplace
```

或者，如果使用 bash 或在 Linux 上，只需执行以下操作：

```
make
```

重新编译。

要运行测试套件，只需运行：

```
pytest kivy/tests
```

或者在 bash 或 Linux 中：

```
make test
```

#### 检查演示

现在应该安装 Kivy。您应该能够在 Python 中运行，或者，如果您安装了 Kivy 示例，则可以运行演示。`import kivy`

在 Windows 上：

```
python kivy_venv\share\kivy-examples\demo\showcase\main.py
```

或者在 bash、Linux 和 macOS 中：

```
python kivy_venv/share/kivy-examples/demo/showcase/main.py
```

Kivy 示例目录的确切路径也存储在`kivy.kivy_examples_dir`.

下面的3d猴子演示`kivy-examples/3Drendering/main.py`也很好看。

### 使用 Conda 安装

如果你使用[Anaconda](https://en.wikipedia.org/wiki/Anaconda\_\(Python\_distribution\))，你可以使用它的包管理器[Conda](https://en.wikipedia.org/wiki/Conda\_\(package\_manager\))安装 Kivy ：

```
conda install kivy -c conda-forge
```

`pip`如果您使用的是 Anaconda，请不要使用它来安装 kivy，除非您是从源代码安装的。

### 安装 Kivy 的依赖项

Kivy 为其核心提供者支持一个或多个后端。例如，它支持 Windows 图形后端的 glew、angle 和 sdl2。对于每个类别（窗口、图形、视频、音频等），必须至少安装一个后端才能使用该类别。

为了便于安装，我们提供了将安装选定后端的`extras_require` [组](https://setuptools.readthedocs.io/en/latest/userguide/dependency\_management.html#optional-dependencies) ，以确保 Kivy 安装正常工作。因此，可以更简单地安装 Kivy，例如\`\`pip install “kivy\[base,media,tuio]”\` [\`](https://kivy.org/doc/stable/gettingstarted/installation.html#id1)。选择器的完整列表和它们安装的包列在 [setup.py](https://github.com/kivy/kivy/blob/master/setup.cfg)中。每个选择器中的确切包在未来可能会发生变化，但每个选择器的总体目标将保持如下所述。

我们提供以下选择器：

> _base_：Kivy 运行所需的最小典型依赖项，
>
> 不包括视频/音频。
>
> _media_：仅 Kivy 所需的视频/音频依赖项
>
> 能够播放媒体。
>
> _full_：Kivy 运行所需的所有典型依赖项，包括视频/音频和
>
> 大多数可选的依赖项。
>
> _dev_：在开发模式下运行 Kivy 所需的所有附加依赖项
>
> （即它不包括 base/media/full 依赖项）。例如，编译所需的任何标头，以及运行测试和创建文档所需的所有依赖项。
>
> _tuio_：使 TUIO 工作所需的依赖项（主要是 oscpy）。

以下选择器在`Kivy_deps`命名空间下安装由 kivy 打包为 wheels 的后端。它们通常会发布和版本化以匹配特定的 Kivy 版本，因此我们提供选择器以方便安装（即，您现在可以为 Kivy 版本自动安装正确的 sdl2 而不是必须执行）。`pip install kivy kivy_deps.sdl2==x.y.zpip install "kivy[sdl2]"`

> _gstreamer_：gstreamer 视频/音频后端（如果可用）
>
> （目前仅适用于 Windows）
>
> _angle_：备用 OpenGL 后端（如果可用）
>
> （目前仅适用于 Windows）
>
> _sdl2_：窗口/图像/音频后端，如果可用（目前仅在 Windows 上，
>
> 在 macOS 和 Linux 上，它已经包含在主 Kivy 轮中）。
>
> _glew_：备用 OpenGL 后端，如果可用（目前仅在 Windows 上）

以下是`kivy_deps`依赖轮：

*   [gstreamer](https://gstreamer.freedesktop.org/)（可选）

    `kivy_deps.gstreamer`是一个可选的依赖项，只需要音频/视频支持。我们只在 Windows 上提供，其他平台需要单独安装。或者，改用[ffpyplayer](https://pypi.org/project/ffpyplayer/) 。
*   [闪光](http://glew.sourceforge.net/)和/或 [角度](https://github.com/Microsoft/angle)

    `kivy_deps.glew`并且`kivy_deps.angle`适用于[OpenGL](https://en.wikipedia.org/wiki/OpenGL)。两者都可以安装，没问题。它仅适用于 Windows。在其他平台上，外部不需要它。

    可以使用环境变量选择其中哪一个用于 OpenGL `KIVY_GL_BACKEND`：通过将其设置为`glew` （默认值）、`angle_sdl2`或`sdl2`。在这里，`angle_sdl2`是一个替代品 `glew`，但`kivy_deps.sdl2`也需要安装。
*   [sdl2](https://libsdl.org/)

    `kivy_deps.sdl2`适用于窗口/图像/音频和可选的 OpenGL。它仅在 Windows 上可用，并包含在其他平台的主要 Kivy wheel 中。

### Python 词汇表

在这里我们解释如何安装 Python 包，如何使用命令行以及什么是轮子。

#### 安装 Python&#x20;

Kivy 是用 [Python](https://en.wikipedia.org/wiki/Python\_\(programming\_language\))编写 的，因此，要使用 Kivy，您需要现有的[Python](https://www.python.org/downloads/windows/)安装。多个版本的 Python 可以并排安装，但 Kivy 需要作为包安装在每个要使用 Kivy 的 Python 版本下。

要安装 Python，请参阅每个平台的说明： [Windows](https://kivy.org/doc/stable/installation/installation-windows.html#install-python-win)、[macOS](https://kivy.org/doc/stable/installation/installation-osx.html#install-python-osx)、 [Linux](https://kivy.org/doc/stable/installation/installation-linux.html#install-python-linux)、[RPi](https://kivy.org/doc/stable/installation/installation-rpi.html#install-python-rpi)。

安装 Python 后，打开[控制台](https://kivy.org/doc/stable/gettingstarted/installation.html#command-line)并通过键入确保 Python 可用。`python --version`

#### 如何使用命令行

要执行此处给出的任何`pip`或`wheel`命令，您需要一个_命令行_（此处也称为_console_、_terminal_、[shell](https://en.wikipedia.org/wiki/Unix\_shell)或[bash](https://en.wikipedia.org/wiki/Bash\_\(Unix\_shell\))，其中最后两个指的是 Linux 风格的命令行）并且 Python 必须在 PATH[上](https://en.wikipedia.org/wiki/PATH\_\(variable\))。

Windows 上的默认命令行是 [命令提示符](http://www.computerhope.com/issues/chusedos.htm)，简称_cmd_。打开它的最快方法是按键盘上的_Win+R 。_在打开的窗口中，键入`cmd`然后按回车键。

我们推荐的 Windows 上的替代 Linux 样式命令行是 [Git for Windows](https://git-for-windows.github.io/)或[Mysys](http://www.mingw.org/wiki/MSYS)。

请注意，即使安装了 bash 终端，仍然可以使用默认的 Windows 命令行。

要临时将 Python 安装添加到 PATH，只需打开命令行，然后使用命令`cd`将当前目录更改为安装 python 的位置，例如.`cd C:\Python37`

如果您使用默认选项安装了 Python，则 Python 的路径将永久存在于您的 PATH 变量中。安装程序中有一个选项可让您执行此操作，默认情况下已启用。

但是，如果 Python 不在您的 PATH 中，请按照以下说明添加它：

* [windows命令行](http://www.computerhope.com/issues/ch000549.htm)使用说明
* [bash 命令行](http://stackoverflow.com/q/14637979)说明

#### 什么是 pip 什么是 wheels

[在 Python 中，可以使用名为pip](https://pip.pypa.io/en/stable/)（“python 安装包”）的python 包管理器安装 Kivy 等包。

从源代码安装时，某些软件包（例如 Kivy）需要额外的步骤，例如编译。

相反，wheels（带`.whl`扩展名的文件）是已经编译过的包的预构建分发版。这些轮子在安装时不需要额外的步骤。

[当pypi.org](https://pypi.python.org/pypi) （“Python 包索引”）上有轮子可用时，可以使用`pip`. 例如，当您在命令行中执行时，这将自动在 PyPI 上找到合适的轮子。`python -m pip install kivy`

直接下载安装wheel时，使用命令 ，例如：`python -m pip install <wheel_file_name>`

```
python -m pip install C:\Kivy-1.9.1.dev-cp27-none-win_amd64.whl
```

#### 什么是 nightly wheels

每天我们都会创建 Kivy 当前开发版本的快照轮（'nightly wheel'）。[您可以在Kivy Github 存储库](https://github.com/kivy/kivy)的 master 分支中找到开发版本 。

与上一个_稳定_版本（我们在上一节中讨论过）相反，nightly wheels 包含对 Kivy 的所有最新更改，包括实验性修复。有关安装说明，请参阅[预发布、预编译的轮子](https://kivy.org/doc/stable/gettingstarted/installation.html#kivy-nightly-install)。

警告

使用最新的开发版本可能存在风险，您可能会在开发过程中遇到问题。如果您遇到任何错误，请报告它们。
