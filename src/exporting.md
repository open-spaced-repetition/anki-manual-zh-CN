# 导出

> 原文：[Exporting - Anki Manual (ankiweb.net)](https://docs.ankiweb.net/exporting.html)

<!-- toc -->

导出功能允许你将集合的一部分保存为文本文件或打包的 Anki 牌组。要导出，请点击「文件」菜单并选择「导
出」。

## 文本文件

如果你选择「纯文本笔记」，Anki 将会把笔记的内容写入一个文本文件中。每个字段由一个制表符分隔。如果你
编辑了生成的文件，并且没有修改第一个字段，则可以稍后将该文件重新导入 Anki，Anki 将根据你的编辑更新笔
记，前提是你导入到相同的笔记模板中。

如果你发现自己也需要编辑第一个字段，则需要更改笔记模板的格式，使第一个字段是一个 ID 号，而不是实际文
本。（你可以安装[添加笔记 ID](https://ankiweb.net/shared/info/8897764) 插件来简化这一过程。）

为了在重新导入文本时保留格式，文本会以嵌入所有 HTML 格式的方式进行导出。

## 打包牌组

一个「打包牌组」由卡片、笔记、笔记模板以及任何声音或图像组成，这些都被打包成一个以 .apkg 或 .colpkg
结尾的文件。你可以使用打包牌组在不同人之间传输卡片，或者备份集合的一部分。

有两种不同类型的打包牌组。

### 集合 (.colpkg)

当你选择导出所有牌组且包含调度信息时，这称为「集合文件」。Anki 将你的整个集合复制到一个以 .colpkg 结
尾的文件中，并将其放置在桌面上。集合文件用于备份你的集合，或将其复制到另一台设备上。

使用旧版本 Anki 创建的集合文件被称为 collection.apkg。

稍后导入此文件时，Anki 会删除集合中的所有当前卡片，并用文件中的项目替换集合。这对于在设备之间来回复
制集合非常有用。

导入集合文件时，集合中现有的媒体不会被删除。要删除未使用的媒体，请使用 工具&gt;检查媒体。

如果你选择 Anki 2.1.50+ 集合文件格式，导入和导出将更快，媒体文件将会被压缩，但生成的 .colpkg 文件将
无法被较旧的 Anki 客户端读取。

### 牌组 (.apkg)

牌组包包含一个牌组（以及它可能包含的任何子牌组）。它们的文件名以 .apkg 结尾，但文件名不同于
collection.apkg。当你导入一个牌组包时，Anki 会将其内容添加到你的集合中，而不是覆盖你的集合。

如果牌组包中的一些笔记之前已被导入，Anki 将保留最近修改时间的版本。因此，如果你下载了一个更新的牌
组，更新版本中所做的编辑会在你的集合中体现出来，但如果在集合中进行了编辑后重新导入一个未更改的牌组，
集合中的更改将会被保留。

如果你选择不包含调度信息，Anki 会假定你在与他人共享牌组，并会清除标记和记忆难点标签，这样他们就会有
一个干净的副本。