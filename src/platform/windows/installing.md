# 在 Windows 上安装和升级 Anki

<!-- toc -->

## 要求

最新的 Anki 版本需要运行 64 位版本的 Windows 10 或 11 的电脑。

- 支持 Windows 7 和 8.1 的最后一个 Anki 版本是 Anki 2.1.49。
- 支持 32 位 Windows 的最后一个 Anki 版本是
  [Anki 2.1.35-alternate](https://github.com/ankitects/anki/releases/tag/2.1.35)。

如果你使用的是老旧的电脑，可以从 [发布页面](https://github.com/ankitects/anki/releases) 获取旧版本。

## 安装

要安装 Anki：

1. 从 <https://apps.ankiweb.net> 下载 Anki。有关如何在 -qt5 和 -qt6 之间进行选择，请参见下一节。
2. 将安装程序保存到桌面或下载文件夹。
3. 双击安装程序运行。如果你看到错误信息，请参见 [安装问题页面](installation-issues.md)。
4. Anki 安装完成后，双击桌面上的新星形图标以启动 Anki。

## Qt5 vs. Qt6

最新版本的 Anki 以 Qt5 和 Qt6 两个不同的版本提供。建议大多数用户使用 Qt6 版本。

Qt6 版本的优点：

- 各种错误修复，包括更好地支持不常见的语言。
- 非常大的图片比 Qt5 版本加载更快。
- 安全更新。Qt5 库的支持于 2020 年 11 月停止，这意味着自那时以来发现的安全漏洞将保持未修复状态。
- 一些用户在 Qt5 中使用[自定义快捷键切换输入语言](https://github.com/ankitects/anki/issues/1105)时会
  遇到冻结的问题。

Qt6 版本的缺点：

- 一些插件目前仅在 Qt5 版本上可用。

## 升级

如果从 Anki 2.1.6+ 升级，无需先卸载旧版本。你只需要在关闭 Anki 后，按照上述安装步骤进行。升级时，你
的卡片会被保留。

如果从 2.1.6 之前的 Anki 版本升级，或者在标准版和替代版之间切换，建议先卸载旧版本，这将移除 Anki 的
程序数据，但不会删除你的卡片数据。

如果你希望降级到以前的版本，请确保你先[降级](http://changes.ankiweb.net)。

## 插件兼容性

一些插件可能无法总是与最新的 Anki 版本兼容。如果你升级到最新 Anki 版本后发现某个不可或缺的插件停止工
作，可以从 [发布页面](https://github.com/ankitects/anki/releases) 下载旧版本的Anki。

## 问题

如果在安装或启动 Anki 时遇到任何问题，请参见以下页面：

- [安装问题](installation-issues.md)
- [启动问题](startup-issues.md)
- [显示问题](display-issues.md)
- [权限问题](permission-problems.md)

如果在使用 Anki 时遇到任何界面问题，请参见以下页面：

- [复制和粘贴问题](copy-and-paste.md)
- [文字大小问题](text-size.md)
