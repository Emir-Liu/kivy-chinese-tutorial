# 绘图

每个小部件都有一个画布，即绘图的位置。画布是一组绘图指令，应该在小部件的图形表示发生更改时执行。

您可以向画布添加两种类型的指令：上下文指令(context instructions)和顶点指令(vertex instructions)。您可以从 Python 代码或 kv 文件（首选方法）中添加指令。如果您通过 kv 文件添加它们，则优点是它们在任何依赖于它们的属性更改时会自动更新。在 Python 中，您需要自己完成此操作。

<figure><img src="https://kivy.org/doc/stable/_images/gs-drawing.png" alt=""><figcaption><p>python代码和kv文件对比</p></figcaption></figure>

无论哪种方式，当小部件的位置或大小发生更改时，MyWidget 的画布都会重新绘制。

您可以使用 [`canvas.before`](https://kivy.org/doc/stable/api-kivy.graphics.html#kivy.graphics.Canvas.before)或 [`canvas.after`](https://kivy.org/doc/stable/api-kivy.graphics.html#kivy.graphics.Canvas.after)组根据您希望执行指令的时间来分隔指令。

如果要深入了解，请查看 Kivy 的图形处理方式
