# 疑难解答

如果你在使用 Anki 的过程中遇到了问题，请按顺序尝试以下步骤：

**1. 重启 Anki**

请关闭 Anki，然后重新启动它。

如果由于错误信息无法关闭 Anki，你可以使用任务管理器终止 Anki，或重启电脑。Anki 会定期保存，所以大多
数情况下你不会损失超过几分钟的工作。

如果问题不再出现，你可以跳过以下步骤。

**2. 检查附加组件**

请关闭 Anki，然后按住 shift 键重新启动。如果问题消失，说明是某个附加组件导致的。移除不需要的附加组
件，并禁用其他一半的附加组件。如果问题持续，尝试禁用另一半。重复该过程，直到找到导致问题的附加组件。
然后请使用复制调试信息按钮将信息粘贴到报告中，报告此问题给附加组件作者。

**3. 检查 Anki 版本**

你可以在 帮助>关于 Anki 或 Anki>关于 Anki 菜单中找到你的版本信息。如果你使用的版本不是发布在
<https://apps.ankiweb.net> 的最新版本，请关闭 Anki，安装最新版本，然后重新启动 Anki，查看问题是否消
失。

如果你使用的是 Linux，请确保能够使用 Anki 网站上提供的打包版本重现错误，因为发行版通常会分发
[损坏的版本](https://anki.tenderapp.com/kb/anki-ecosystem/third-party-linux-packages-and-source-builds-are-not-supported)。

**4. 检查数据库**

重启 Anki 后，请尝试使用工具>检查数据库菜单项，确保你的集合没有任何问题。

**5. 重启电脑**

有时重启电脑可能会有所帮助。

**6. 更改视频驱动程序**

崩溃和显示问题可能是由视频驱动程序导致的。尝试在首选项屏幕中或通过 gldriver 文件切换不同的视频驱动程
序可能会有帮助。确保尝试所有三个选项。

- [Windows](https://docs.ankiweb.net/platform/windows/display-issues.html)
- [Mac](https://docs.ankiweb.net/platform/mac/display-issues.html)
- [Linux](https://docs.ankiweb.net/platform/linux/display-issues.html)

**7. 重置窗口大小**

有时在启动 Anki 后立即按下首选项屏幕中的「重置窗口大小」按钮会有所帮助。

**8. 如果问题仍然存在**

如果你确认使用的是最新的 Anki 版本，并且在按住 shift 键启动 Anki 时仍然出现错误，
请[报告问题](./getting-help.md)，在你的帖子中包含你接收到的下一个错误信息。
