# Windows 启动问题

> 原
> 文：[Startup Issues - Anki Manual (ankiweb.net)](https://docs.ankiweb.net/platform/windows/startup-issues.html)

<!-- toc -->

## 没有错误，但应用未出现

最近有一些报告称 Anki 无法出现，但没有显示任何错误消息。如果你遇到这种情况，你可以：

- 一些用户报告在断开多个/外部显示器后问题停止。
- 安装[最新的 Anki 版本](https://apps.ankiweb.net/)（尝试 qt6 和 qt5）
- 或者你可以尝试
  [调整小数点分隔符](https://forums.ankiweb.net/t/windows-update-broke-anki/1822/75)，如果它不是一个
  点。
- 或者你可以尝试旧版的 Anki 2.1.35-alternate 构建。

## Windows 更新

启动 Anki 时，你可能会收到如下消息：

- _Error loading Python DLL_
- _The program can't start because api-ms-win.... is missing_
- _Failed to execute script runanki_
- _Failed to execute script pyi_rth_multiprocessing_
- _Failed to execute script pyi_rth_win32comgenpy_

这些错误通常是因为你的计算机缺少 Windows 更新或 Windows 库。

请打开 Windows 更新，并确保你的系统已安装所有更新。如果有需要安装的，请在安装后重启你的设备。

## Windows 7/8

在 Windows 7/8 上，你可能需要手动安装额外的更新。请尝试：

- <https://www.microsoft.com/en-us/download/details.aspx?id=48234>
- <https://aka.ms/vs/15/release/vc_redist.x64.exe>
- <http://www.catalog.update.microsoft.com/Search.aspx?q=kb4474419>
- <http://www.catalog.update.microsoft.com/Search.aspx?q=kb4490628>

## 视频驱动问题

请参阅[显示问题](./display-issues.md)。

## 多显示器

如果你收到 _LoadLibrary failed with error 126_，这可能是因为 Anki 构建所使用的工具包
在[多显示器](https://forums.ankiweb.net/t/error-126-on-open-anki-desktop/13967)上遇到了问题。

## 杀毒软件/防火墙软件

你电脑上的第三方软件可能阻止 Anki 加载。你可以尝试将 Anki 添加为例外，或者暂时禁用你的杀毒软件/防火
墙，看看是否有帮助。

## 管理员权限

一些用户报告说，Anki 在他们右键点击 Anki 图标并选择「以管理员身份运行」之前无法运行。Anki 将其所有数
据存储在用户文件夹中，通常不需要管理员权限，但如果你已经尝试了其他方法，可以试试这个。

## 更新后存在多个 Anki 安装

如果更新过程导致你有多个 Anki 安装（例如在 `C:\Program Files\Anki` 和
`C:\Program Files (x86)\Anki`），它们可能处于不可用状态，而 Anki 可能拒绝启动且不显示任何错误消息。

你可以尝试卸载所有版本 - 你可以通过 Windows 的「应用和功能」设置菜单，或在每个 Anki 程序文件夹中运行
`uninstall.exe` 来做到这一点。然后，再次安装 Anki。

## 调试

从终端启动 Anki 可能会揭示更多关于某些错误的信息。在安装最新的 Anki 版本并确保所有 Windows 更新安装
后，不要直接运行 Anki，使用「开始>运行」，并键入 cmd.exe。当控制台窗口出现时，输入

```bat
cd \program files\anki & anki-console
```

推测 Anki 将像之前一样无法打开，但可能会揭示导致问题的原因。

## 如果一切都失败

如果在尝试上述解决方法后仍无法启动 Anki，你还有两个选择：

- 你可以尝试[从 Python 运行](https://faqs.ankiweb.net/running-from-python.html)。
- 你可以尝试使用旧工具包构建的旧版 Anki，如 2.1.35-alternate 和 2.1.15。
