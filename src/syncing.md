# 与 AnkiWeb 同步

> 原文：[Syncing with AnkiWeb - Anki Manual](https://docs.ankiweb.net/syncing.html)

<!-- toc -->

AnkiWeb 是一项服务，允许你在多个设备上保持你的集合同步，并在线学习。请在按照以下步骤操作之前注册一
个[免费账户](https://ankiweb.net/)。

## 入门视频

要快速了解同步，请查
看[同步介绍视频](https://www.youtube.com/watch?v=YkiM4DPzSVc&list=PLGgmaKOIHykFoomqkBJAyGiDQ2kyiuTao&yt:cc=on)。

## 设置

要开始在设备之间同步你的集合，请点击同步按钮（在[主界面](studying.md#牌组)的右上角），或按键盘上的
'y'。系统会要求输入你在注册过程中创建的 AnkiWeb ID 和密码。

当你第一次同步集合时，Anki 会询问你是要上传还是下载。如果你在计算机上有卡片，而你的 AnkiWeb 账户为
空，请选择「上传」以将数据发送到 AnkiWeb。如果你在 AnkiWeb 上有来自其他设备的卡片，而你的计算机上没
有卡片，请选择「下载」以用 AnkiWeb 上的卡片替换空的本地集合。如果两个设备上有不同的卡片，将需
要[进行更多工作](#合并冲突)以避免数据丢失。

一旦初始的单向同步完成，Anki 将能够合并来自多个位置的更改，但有一些例外情况。

如果在同一台设备上有多人使用 Anki，并且为每个用户创建了个人资料，则每个用户都需要创建自己的 AnkiWeb
账户以进行同步。如果尝试用单个 AnkiWeb 账户同步多个个人资料，你将丢失数据。

## 自动同步

启用同步后，Anki 每次关闭或打开集合时将自动同步。如果你更喜欢手动同步，可以在 Anki
的[首选项](preferences.md#同步)中禁用自动同步。

## 按钮颜色

当需要正常同步时，同步按钮将变为蓝色；当需要完全同步时，将变为红色。

## 媒体

相关视频：<https://www.youtube.com/watch?v=phP9GGG-PxY>

Anki 将同步你的笔记中使用的任何声音和图像。它会注意到何时在你的[媒体文件夹](files.md#文件位置)中添
加、删除或替换了媒体，但如果你对现有文件进行了编辑，它不会注意到。要使你的编辑被同步，你需要同时添
加、删除或替换一个文件。

单向同步（提示你上传或下载）对媒体同步没有影响——媒体更改总是会被合并。

为防止意外数据丢失，删除操作只有在媒体完全同步后才会同步到其他设备。如果你在设备完全同步前删除文件，
而已经在 AnkiWeb 上的文件则会在下次同步时被下载。

如果你不小心删除了媒体文件，并希望恢复它们，请打开首选项并注销。下次同步时，如果 AnkiWeb 上仍然有可
用文件，Anki 将恢复任何已删除的文件。

如果你在使用 [USB 闪存驱动器](files.md#从闪存驱动器运行)上运行 Anki，你应该使用 NTFS 文件系统，因为
Anki 可能无法检测到 FAT32 文件系统上的媒体更改。

## 冲突

相关视频：<https://www.youtube.com/watch?v=UEAcpfMQnjo>

在正常情况下，复习和笔记编辑是可以合并的，因此如果你在同步前在两个不同的设备上进行了复习或编辑，Anki
将保留你在两个位置的更改。如果同一张卡片在两个不同位置被复习，两个复习都会在复习历史中标记，卡片将保
持在最新被回答时的状态。

有某些更改是 Anki 无法合并的。这些主要与笔记的格式有关：比如添加新字段或删除卡片模板。当你执行不能合
并的操作时，Anki 会警告你，并让你选择是否中止操作。如果选择继续，下次同步时你需要选择保留本地副本还
是 AnkiWeb 上的副本。

如果在同步时检测到某些问题，也会强制进行单向同步。如果你发现这种情况持续发生，请在我们的支持网站上发
帖。

当需要单向同步时，你需要选择是保留本地设备上的集合，还是 AnkiWeb 上的集合。如果两端都有更改，则只能
保留一端的更改。

如果选择上传，本地设备上的内容将发送到 AnkiWeb。然后，你需要同步其他设备，并选择「下载」以让它们获取
该内容的副本。

如果选择下载，它将用 AnkiWeb 上的数据替换你所做的任何本地更改。

一旦所有设备同步，未来的同步将恢复到正常的合并更改行为。

如果你希望强制进行完整上传或下载（例如，因为不小心在一侧删除了牌组，并想恢复牌组而不是同步删除操
作），你可以在「工具>首选项>同步」勾选「下次同步时，强制单向覆盖」框，然后正常同步。（你将被询问选择
要使用哪一侧。）

强制单向同步只影响卡片同步——媒体正常同步。如果你有要从 AnkiWeb 中删除的文件，请确保你的客户端已完全
同步。同步最新后，你删除的任何文件（例如通过检查媒体功能）将在接下来的同步中从 AnkiWeb 中删除。

## 合并冲突

因为[首次同步](#设置)只能进行单方向同步，如果在设置同步之前，你在不同设备或个人资料上添加了不同内
容，如果将一台设备上的内容覆盖另一台设备的内容，一个设备上的内容将丢失。在经过一些工作后，可以手动将
数据合并到一个集合中。

首先，在每个设备/个人资料上进行备份，以防出现问题。在计算机版本中，你可以通过「文件>导出」导出「所有
牌组」，包括调度信息和媒体文件，并将文件保存在安全的地方。在 AnkiMobile 上，牌组列表界面上的添加/ 导
出按钮将允许你导出包含媒体的所有牌组。

接下来，如果你的设备之一是移动设备，首先同步它。如果有冲突，选择「上传」以用移动设备的数据覆盖
AnkiWeb 上的任何现有数据。如果两个设备/个人资料都在你的计算机上，首先同步拥有最多牌组的设备/个人资
料。

现在返回到另一个设备/个人资料。如果启用了自动同步，可能会弹出一个消息，询问你是否要上传或下载。单击
取消按钮——我们现在不想同步。

一旦看到牌组列表，点击第一个牌组旁边的齿轮图标，然后选择「导出」。导出包括调度信息和媒体的内容，并将
.apkg 文件保存在某处。现在你需要为每个顶级牌组重复此操作。

一旦所有顶级牌组导出完成，点击右上角的同步按钮，选择「下载」，这将用你从另一设备同步的内容覆盖本地内
容。

现在，你可以使用「文件>导入」来导入你之前导出的 .apkg 文件，这将合并导出的内容和现有内容，因此所有内
容将集中在一处。

## 防火墙

Anki 需要能够建立出站 HTTPS 连接以进行同步。它必须能够连接到 ankiweb.net、
sync.ankiweb.net、sync2.ankiweb.net 等。这些域名可能会随时间变化，它们指向的 IP 地址也可能会更改，因
此我们建议你允许 \*.ankiweb.net 的通配符访问，减少将来防火墙规则需要更新的可能性。

如果你的设备上有防火墙，你应为 Anki 添加一个例外。如果你在工作或学校网络上，请联系你的网络管理员寻求
帮助——我们无法为你提供帮助。

## 代理

如果你需要代理才能访问互联网，Anki 应自动拾取你的系统代理设置（如果你使用的是 Windows 或 macOS），并
在其他平台上遵循 HTTP_PROXY 环境变量。

Anki 只能在手动配置代理且不需要密码时拾取你的系统设置。如果你的系统使用自动代理设置，或使用需要用户
名和密码的代理，你需要手动告诉 Anki 代理配置。

要告诉 Anki 你的代理设置，请定义一个指向代理服务器的 HTTPS_PROXY 环境变量。它看起来像这样：

http://user:pass@proxy.company.com:8080

如果你的用户名或密码包含 @（例如 `user@workdomain.com`），则需要将其更改为 %40，如下所示：

http://user%40workdomain.com:pass@proxy.company.com:8080

Anki 2.0 期望找到 HTTP_PROXY 而不是 HTTPS_PROXY。

要在 Windows 上设置环境变量，请参见
<https://www.google.com/search?q=windows+set+environmental+variable>

如果你使用的是 Mac，请参见
<http://stackoverflow.com/questions/135688/setting-environment-variables-in-os-x>

严格限制的网络会拦截安全连接并呈现其自己的证书，这可能导致 Anki 出现 SSL 错误。在这种环境中，你可能
可以通过[这个插件](https://ankiweb.net/shared/info/1332261690)解决错误。

另一个解决方案是安装一个本地代理服务器，并将该代理服务器指向你通常使用的代理服务器。然后你可以告诉
Anki 使用本地代理，该代理将请求重定向到你通常使用的代理。
