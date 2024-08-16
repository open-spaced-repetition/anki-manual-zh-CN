# Anki 在 Gnome/Linux 上未应用 GTK 主题

> 原
> 文：[Incorrect GTK Theme - Anki Manual (ankiweb.net)](https://docs.ankiweb.net/platform/linux/gtk-theme.html)

你可以通过明确告诉 Anki GTK 主题是什么来解决这个问题。在终端中运行以下命令：

```shell
theme=$(gsettings get org.gnome.desktop.interface gtk-theme)
echo "gtk-theme-name=$theme" >> ~/.gtkrc-2.0
echo "export GTK2_RC_FILES=$HOME/.gtkrc-2.0" >> ~/.profile
```

然后注销并重新登录你的计算机，Anki 应该就能应用 GTK 主题了。
