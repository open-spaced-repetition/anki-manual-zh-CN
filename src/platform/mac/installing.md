# 在 macOS 上安装和升级 Anki

<!-- toc -->

## 要求

新版 Anki 需要运行 macOS 10.13.4 或更高版本的 Mac。

支持 macOS 10.10 到 10.13.3 的最后一个 Anki 版本 是
[Anki 2.1.35-alternate](https://github.com/ankitects/anki/releases/tag/2.1.35)。如果你使用较旧的机
器，可以从[发布页](https://github.com/ankitects/anki/releases) 获取旧版本。

## 安装

1. 从 <https://apps.ankiweb.net> 下载 Anki。请参见下一节了解如何在 -qt5 和 -qt6 之间进行选择。
2. 将文件保存到桌面或下载文件夹。
3. 打开它，然后将 Anki 拖动到应用程序文件夹或桌面。
4. 在放置 Anki 的位置双击它。

## Qt5 vs. Qt6

新版本的 Anki 有单独的 Qt5 和 Qt6 变体。对于大多数用户，推荐使用 Qt6 版本。

Qt6 版本的优点：

- 对新款 Apple Silicon Mac 的原生支持（更快，更好的电池寿命）。
- 各种漏洞修复，包括更好地支持不常见的语言。
- 安全更新。Qt5 库的支持在 2020 年 11 月被终止，这意味着自那以后发现的任何安全漏洞将不会被修复。

Qt6 版本的缺点：

- 不能再使用标签页窗口（例如在全屏幕时）。
- 一些 Mac 用户报告说 Intel Qt5 版本对他们来说更快且更可靠。
- 一些插件目前仅适用于 Qt5 版本。

## 升级

要升级，关闭 Anki（如果它已打开），然后按照上述步骤操作。将 Anki 图标拖放到之前存放它的同一位置，然
后在系统提示时覆盖旧版本。你的卡片数据将会保留。

## Homebrew

[Homebrew](https://brew.sh/) 用户可以通过 `brew install --cask anki` 在他们喜好的终端应用中安装
Anki。

升级可以通过 `brew upgrade` 完成，卸载可使用：`brew uninstall --cask anki`

## 插件兼容性

某些插件可能不总是与最新的 Anki 版本兼容。如果你升级到最新的 Anki 版本后发现有不可或缺的插件无法工
作，你可以从[发布页](https://github.com/ankitects/anki/releases) 下载旧版本的Anki。

## 问题

如果在安装或启动 Anki 时遇到任何问题，请参见：

- [显示问题](display-issues.md)
