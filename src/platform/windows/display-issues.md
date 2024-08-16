# Windows 显示问题

> 原
> 文：[Display Issues - Anki Manual (ankiweb.net)](https://docs.ankiweb.net/platform/windows/display-issues.html)

<!-- toc -->

在 Windows 上，有三种内容显示在屏幕上的方式。默认是 _software_，它比较慢， 但兼容性最强。另有两种更
快的选项：_OpenGL_ 和 _ANGLE_。它们速度更快，但可能不能正常工作， 或者可能导致如菜单栏缺失、窗口空白
等显示问题。哪一种效果最好取决于你的电脑。

是否及如何更改此显示方法取决于你使用的 Anki 版本，更具体地说，取决于使用的 Qt 工具包 版本。

## Qt5

此工具包用于所有 2.1.50 之前的 Anki 版本。这里，显示驱动可以通过工具>首选项菜单进行调整。确保在调整
后重启 Anki。

如果你无法打开 Anki 的首选项屏幕，重启 Anki 几次也没用，可能需要手动调整图形驱动。你可以通过启动
cmd.exe 并输入以下命令来完成：

```bat
echo auto > %APPDATA%\Anki2\gldriver
```

它不会输出任何信息。然后，你可以再次启动 Anki。

默认是 `software`；你可以尝试的其他两个驱动是 `angle` 和 `auto`。

## Qt6

Anki 2.1.50+ 提供了更先进的 Qt6 工具包。新工具包默认启用了图形加速。如果你遇到显示问题，可以尝试通过
命令行切换到 software 模式：

```bat
echo software > %APPDATA%\Anki2\gldriver6
```

或者通过 PowerShell：

```powershell
echo software > $env:APPDATA\Anki2\gldriver6
```

它不会输出任何信息。然后，你可以再次启动 Anki。

要恢复默认行为，将 `software` 改为 `auto`，或者删除该文件。

在 Anki 23.10+ 中，你也可以从首选项屏幕中更改图形驱动。

## 全屏

Anki 2.1.50+ 带有全屏模式，但由于各种问题，使用 `OpenGL` 时必须禁用它。按照上述描述开启软件渲染后，
可以使用全屏选项，但请注意渲染性能可能会下降。

在 Anki 23.10+ 中，全屏模式默认支持使用 Direct3D 驱动。
