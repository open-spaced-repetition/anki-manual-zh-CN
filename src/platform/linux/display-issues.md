## 在 Linux 上的显示问题

> 原
> 文：[Display Issues - Anki Manual (ankiweb.net)](https://docs.ankiweb.net/platform/linux/display-issues.html)

### Qt5

硬件加速默认是关闭的。在偏好设置屏幕中启用它并重启 Anki 可能会让 Anki 的界面响应更加灵敏，但有些用户
在启用时可能会遇到菜单栏缺失、窗口空白或崩溃的问题。（窗口空白也可能由
[这个问题](./blank-window.md)引起。）

你可以在 Anki 的偏好设置屏幕中调整显示驱动。我们建议你尝试两种设置，看看哪一种对你最合适。

如果你无法打开 Anki，可以在终端中通过将 `auto` 或 `software` 写入 `~/.local/share/Anki2/gldriver` 来
调整驱动。请注意，如果你使用的是 nouveau，它已知有一些问题，而且只支持软件模式。

### Qt6

硬件加速默认是开启的。如果你遇到空白屏幕或显示问题，可以尝试使用终端启用软件渲染：

```
echo software > ~/.local/share/Anki2/gldriver6
```

如果你希望切换回默认设置，将 `software` 改为 `auto`，或删除该文件。

在 Anki 23.10+ 版本中，你还可以从偏好设置屏幕中更换图形驱动。
