# 在 Linux 上安装和升级 Anki

> 原
> 文：[Install & Upgrade - Anki Manual (ankiweb.net)](https://docs.ankiweb.net/platform/linux/installing.html)

<!-- toc -->

## 要求

封装版本要求近期的 64 位 Intel/AMD Linux，同样需要 glibc 和一些通用库，如 libwayland-client 和
systemd。如果你使用的是不同的架构（例如 ARM/AArch64），或是一个精简的 Linux 发行版，你将无法使用封装
版本，但你可以尝试使用 [Python wheels](https://betas.ankiweb.net/#via-pypipip)。

Debian 及其衍生版本，例如 Ubuntu
和[启用 Linux 的 Chromebook](https://support.google.com/chromebook/answer/9145439?)，请在安装前使用
以下命令：

```shell
sudo apt install libxcb-xinerama0 libxcb-cursor0 libnss3
```

如果安装后 Anki 无法启动，你可能[缺少其他库](./missing-libraries.md)。

如果你在 Ubuntu 24.04 上无法启动 Anki，请参
见[本主题](https://forums.ankiweb.net/t/issues-running-on-ubuntu-24-04/40974)。

Anki 的构建系统仅支持 glibc，因此目前不支持基于 musl 的发行版。

## 安装

安装 Anki 的步骤：

1. 从 <https://apps.ankiweb.net> 下载 Anki 到你的 Downloads 文件夹。有关如何在 -qt5 和 -qt6 之间进行
   选择，请参见下一节。
2. 如果你的系统上尚未安装 zstd，请安装它（例如 `sudo apt install zstd`）。
3. 打开终端并运行以下命令，根据需要替换文件名。

```shell
tar xaf Downloads/anki-2XXX-linux-qt6.tar.zst
cd anki-2XXX-linux-qt6
sudo ./install.sh
```

在某些 Linux 系统上，你可能需要使用 `tar xaf --use-compress-program=unzstd`。

4. 然后，你可以通过输入「anki」并按回车键来启动 Anki。如果遇到任何问题，请参见左侧的链接。

## Qt5 与 Qt6

近期的 Anki 版本有 Qt5 和 Qt6 两个变体。对于大多数用户，推荐使用 Qt6 版本。

Qt6 版本的优点：

- 兼容近期的 glibc 版本（修复[近期发行版上的空屏问题](./blank-window.md)）。
- 更好的 HiDPI 支持。
- 更好的 Wayland 支持。
- 各种错误修复，包括更好地支持不常见语言等。
- 安全更新。Qt5 库的支持已于 2020 年 11 月停止，意味着自那时起发现的任何安全漏洞都将得不到修复。

Qt6 版本的缺点包括：

- 一些插件目前仅在 Qt5 版本上可用。

## 升级

如果你过去是从 .deb/.rpm 等安装 Anki，请确保在安装此处提供的封装包之前删除系统版本。

如果你是从之前的封装包升级，只需重复安装步骤，即可升级到最新版本。你的用户数据将会被保留。

如果你希望降级到先前的版本，请确保你先进行[降级](http://changes.ankiweb.net)。

## 插件兼容性

某些插件可能不总是与最新的 Anki 版本兼容。如果你升级到最新的 Anki 版本并发现你不能没有的插件停止工
作，你可以从[发布页面](https://github.com/ankitects/anki/releases)下载旧版本的Anki。

## 问题

如果在安装或启动 Anki 时遇到任何问题，请参见以下页面：

- [缺少库](missing-libraries.md)
- [显示问题](display-issues.md)
- [空白主窗口](blank-window.md)
- [Linux 发行版封装包](distro-packages.md)
- [错误的 GTK 主题](gtk-theme.md)
- [Wayland](wayland.md)
- [输入法](input-methods.md)
