# 文字大小

> 原
> 文：[Text Size - Anki Manual (ankiweb.net)](https://docs.ankiweb.net/platform/windows/text-size.html)

如果你发现文字大小不合适，可以尝试以下两个环境变量：

- ANKI_NOHIGHDPI=1 会关闭部分 Qt 的高 DPI 支持

- ANKI_WEBSCALE=1 会改变 Anki 的网页视图比例（比如牌组列表、学习屏幕等），但保留菜单栏等界面元素不
  变。将 1 替换为所需的比例，例如 1.5 或 0.75。

在 Windows 上，你可以将这些添加到一个批处理文件中，以便于启动 Anki。例如，在桌面上创建一个名为
startanki.bat 的文件，内容如下：

```
set ANKI_WEBSCALE=0.75
start "Anki" "C:\Program Files\Anki\anki"
```

保存后，你可以双击该文件以使用该设置启动 Anki。
