# Wayland

> 原文：[Wayland - Anki Manual (ankiweb.net)](https://docs.ankiweb.net/platform/linux/wayland.html)

从 Anki 2.1.48 开始，你可以通过在启动 Anki 之前定义 ANKI_WAYLAND=1 来强制 Anki 使用 Wayland。Wayland
可能会在多个显示器上为你提供更好的渲染效果，但由于以下问题，目前它默认是关闭的：

- 在某些发行版上，窗口会被渲染得没有边框。
- 无法将窗口置于前面，例如，点击添加以显示现有的添加卡片窗口将不起作用。