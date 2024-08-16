# 贡献

<!-- toc -->

## 公开分享牌组

要向公众分享牌组，请先将它们与 AnkiWeb [同步](syncing.md)，然后登录 AnkiWeb，点击你想分享的牌组旁边
菜单中的「分享」。

如果你之前分享过一个牌组（包括使用旧版本的 Anki），你可以通过点击上述「分享」来更新它。更新一个已分
享的牌组不会重置下载计数或评分。你可以使用已分享牌组页面上的删除按钮来删除你上传的牌组。

在更新牌组时，AnkiWeb 期望牌组的位置与之前相同。例如，假如你分享了一个名为「Korean Verbs」的牌组，然
后将其重命名为「Korean::Korean Verbs」，重新分享将无法更新现有副本。如果你忘记了最初的名字，可以通过
在 AnkiWeb 上下载该牌组并在新的配置文件中导入它（文件 > 导入）（文件 > 切换配置文件 > 添加），来猜测
它。然后你可以复制首次共享时的确切牌组名称。如果这不奏效，请联系支持。

当你更新一个已分享的牌组时，之前下载了该牌组的用户不会自动接收到更新。如果他们再次下载并重新导入该牌
组，新添加的内容将会被导入，而不会改变他们现有的学习进度，只要你和用户都未对笔记类型做出过更改。

## 私密分享牌组

如果你希望将牌组分享给有限的一群人（例如学习小组或班级）而不是向公众分享，你可以在 AnkiWeb 之外进行
分享。

要私密分享牌组，请转到文件菜单并选择导出。选择单个牌组（而不是「所有牌组」），并关闭「包含计划信
息」。这将生成一个 .apkg 文件，你可以与他人分享。

你可以通过邮件将 .apkg 文件发送给他人，将其放到网站或共享文件夹中，或者使用诸如 Dropbox 或 Google
Drive 等免费的文件共享服务，并将链接发送给其他人。

计算机版本和移动客户端通过点击或点击 .apkg 文件，便于导入。然而，AnkiWeb 不支持导入 .apkg 文件，因此
牌组接收者需要拥有计算机版本或移动设备上的 Anki。

当用户导入一个 .apkg 文件时，其集合中已经存在的卡片会被忽略，任何新卡片将被添加。只要他们使用相同的
笔记类型，已修改的卡片也将被更新。为了防止数据丢失，新 .apkg 文件中删除的卡片不会在用户的集合中被删
除，因此如果你需要无论什么原因删除用户牌组中的卡片，你需要与他们联系。

## 分享插件

请参见 <https://addon-docs.ankiweb.net/sharing.html>

## 翻译 Anki

请参见 <https://translating.ankiweb.net>

## 贡献代码

Anki 的源代码位于 <https://github.com/ankitects/anki>

在贡献之前，请参见
[contributing.md](https://github.com/ankitects/anki/blob/main/docs/contributing.md)。