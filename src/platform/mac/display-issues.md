# macOS 上的显示问题

> 原
> 文：[Display Issues - Anki Manual (ankiweb.net)](https://docs.ankiweb.net/platform/mac/display-issues.html)

<!-- toc -->

## Qt6 视频驱动

如果你在 Anki 23.10+ 上遇到显示问题或崩溃，可以尝试在首选项屏幕中更改视频驱动，然后重启 Anki。

旧版本的 Anki 没有在首选项中提供这个选项，但允许你通过打开终端.app，然后粘贴以下内容并点击回车来调整
驱动：

```
echo software > ~/Library/Application\ Support/Anki2/gldriver6
```

它不会输出任何东西。然后你可以重新启动 Anki。

如果你希望切换回默认设置，将 `software` 更改为 `auto`，或者删除该文件。

## 外接 GPU

如果在 Mac 上使用外接显卡时遇到空白屏幕问题，你可以按住 ctrl 键并点击 Anki 应用，选择「显示简介」，
然后启用「优先使用外接 GPU」选项。

## 不同分辨率的显示器

请查看[这个论坛帖子](https://forums.ankiweb.net/t/mac-known-issues-wording-suggestion/7331)。
