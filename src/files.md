# 管理文件和你的集合

> 原文：[Managing Files - Anki Manual (ankiweb.net)](https://docs.ankiweb.net/files.html)

<!-- toc -->

## 检查你的集合

偶尔检查一下你的集合文件是否有问题是个好主意。你可以通过工具菜单中的检查数据库项来执行这项操作。检查
数据库可以确保文件没有损坏，重建一些内部结构，并优化文件。

当你检查数据库时，你的标签列表也会被重建。当你删除单个牌组或卡片时，Anki 不会更新使用过的标签列表，
因为这样做效率不高。如果你想清除列表中不再使用的旧标签，检查数据库是实现这一目的的办法。

请注意，Anki 每两周会自动优化你的集合。这种优化可以确保集合的良好性能，但是在自动优化时并不会检查错
误或重建标签列表。

## 文件位置

在 **Windows** 上，最新版的 Anki 会将你的 Anki 文件储存在应用数据文件夹中。你可以通过打开文件管理
器，并在位置字段中输入 `%APPDATA%\Anki2` 来访问它。旧版本的 Anki 将你的 Anki 文件储存在 `Documents`
文件夹中的一个名为 `Anki` 的文件夹中。

在 **Mac** 电脑上，最近的 Anki 版本将所有文件储存在 `~/Library/Application Support/Anki2` 文件夹中。
该文件夹默认是隐藏的，但可以通过在 Finder 中按住 option 键并点击前往菜单来显示。如果你使用的是旧版
Anki，你的 Anki 文件会在 `Documents/Anki` 文件夹中。

在 **Linux** 上，最近的 Anki 版本会将数据储存在 `~/.local/share/Anki2` 中，或者如果你设置了自定义数
据路径，则储存在 `$XDG_DATA_HOME/Anki2` 中。旧版本的 Anki 会将文件储存在 `~/Documents/Anki` 或
`~/Anki` 中。

在 Anki 文件夹中，会有程序级别和配置文件级别的偏好设置储存在一个名为 prefs.db 的文件中。

每个配置文件都有一个单独的文件夹。该文件夹包含：

- 你的笔记、牌组、卡片等数据保存在名为 collection.anki2 的文件中

- 你的音频和图像保存在 collection.media 文件夹中

- 一个备份文件夹

- 一些系统文件

你不应该在 Anki 打开的情况下复制或移动你的集合。这样做可能会导致你的集合损坏。请也不要移动或修改文件
夹中的其他文件。

## 启动选项

如果你在一台电脑上进行了破坏性的更改，而在另一台电脑上有未损坏的副本，你可能希望在不进行同步的情况下
启动 Anki，以便使用完整的同步选项而不需要先下载更改。同样地，如果你在使用 Anki 时遇到问题，你可能希
望（或被指示）暂时禁用插件，以查看是否有插件导致了问题。你可以在启动 Anki 时按住 <kbd>Shift</kbd> 键
来执行这两个操作。

在启动期间指定自定义文件夹位置是可能的。这是一个主要用于便携安装的高级功能，我们建议你在大多数情况下
使用默认位置。

指定备用文件夹的语法如下：

    anki -b /path/to/anki/folder

- 如果你有多个配置文件，你可以传递 -p &lt;name&gt; 来加载一个特定的配置文件。
- 如果你传递 -p some-fake-name，Anki 将在启动时显示配置文件屏幕。如果没有提供配置文件，将加载最后使
  用的配置文件。

- 要更改界面语言，请使用 -l &lt;iso 639-1 language code&gt;，例如 "-l ja" 表示日语。

如果你总是想使用自定义文件夹位置，你可以修改 Anki 的快捷方式。在 Windows 上，右键点击快捷方式，选择
属性，选择快捷方式选项卡，然后在程序路径后添加 "-b \\path\\to\\data\\folder"，这样应该会给你类似于

    "C:\Program Files\Anki\anki.exe" -b "C:\AnkiDataFolder"

的结果。

你也可以将这种技术与 -l 选项结合使用，以便轻松在不同语言中使用 Anki。

在 Windows 上，应使用反斜杠 (\\) 而不是正斜杠 (/)。

在 Mac 上，没有简单的方法来在点击 Anki 图标时改变行为，但可以从终端启动 Anki 并使用自定义基文件夹：

    open /Applications/Anki.app --args -b ~/myankifolder

另一种方法是定义环境变量 "ANKI_BASE"。在 Windows 上，你可以定义这个环境变量如下：

    set "ANKI_BASE=C:/path/to/AnkiDataFolder"

在 Linux 和 macOS 上，你可以使用：

    export ANKI_BASE="/path/to/AnkiDataFolder"

## DropBox 和文件同步

我们不建议你直接使用第三方同步服务同步你的 Anki 文件夹，因为在文件使用中进行同步会导致数据库损坏。

如果你只是想同步媒体，可以将外部文件夹链接到像 DropBox 这样的服务中。请参阅 [DropboxWiki：同步
Dropbox 以外的文件夹
(archive.org)][http://web.archive.org/web/20180919153730/http://www.dropboxwiki.com/tips-and-tricks/sync-other-folders]
了解更多信息。

如果你还希望保持集合同步，强烈建议你创建一个脚本，将文件从同步文件夹复制到本地文件夹，启动 Anki，然
后在 Anki 关闭后将文件复制回去。这样可以确保文件在打开时不会被同步。

## 网络文件系统

我们强烈建议你将 Anki 文件存储在本地硬盘上，因为网络文件系统可能导致数据库损坏。如果网络文件系统是你
唯一的选择，建议经常使用工具菜单中的检查数据库来检测损坏。

## 从闪存驱动器运行

在 Windows 上，Anki 可以安装在 USB / 闪存驱动器上，并作为便携应用程序运行。下面的示例假设你的 USB 驱
动器是 G 盘。

- 将 \\Program Files\\Anki 文件夹复制到闪存驱动器，这样你会有一个像 G:\\Anki 的文件夹。

- 创建一个名为 G:\\anki.bat 的文本文件，包含以下文本：

  g:\anki\anki.exe -b g:\ankidata

如果你希望防止黑色命令提示窗口保持打开状态，你可以改用以下命令：

    start /b g:\anki\anki.exe -b g:\ankidata

- 双击 anki.bat 应该会启动 Anki，并将用户数据存储在 G:\\ankidata 中。

需要完整路径，包括驱动器号 - 如果你尝试使用 `\anki\anki.exe` 进行同步，它将无法工作。

如果你的闪存驱动器格式为 FAT32，AnkiWeb 上的媒体同步可能不起作用。请将驱动器格式化为 NTFS 以确保媒体
能正确同步。

## 备份

请参阅[本节](./backups.md)。

## 硬盘无法访问

如果 Anki 无法写入 [Anki 文件夹](#文件位置)中的文件，启动时会显示一条消息，表示 Anki 无法写入硬盘，
并将关闭。如果你不确定如何修复权限，请联系对计算机有知识的人来帮你。

## 临时文件夹权限

Anki 使用系统的临时文件夹来存储临时数据。如果该文件夹的权限被恶意应用或有缺陷的杀毒软件更改过，Anki
将无法正常运行。

如果你在 Windows 7 机器上，解决问题的一般步骤如下。由于这有些复杂，如果你不确定，请询问对 Windows 知
识丰富的人。

1. 点击开始栏，输入 %temp%（包括百分号），然后按 <kbd>Enter</kbd>。

2. 返回上一文件夹，定位到 temp 文件夹。右键点击它，然后选择属性。

3. 在安全选项卡中，点击高级。

4. 点击所有者选项卡。如果你不是所有者，点击按钮获取所有权。

5. 在权限选项卡，确保你有完全控制权限。在默认的 W7 安装中，控制实际上是由 c:\\users\\your-username
   继承的。

## 损坏的集合

Anki 使用一个防止程序和计算机崩溃的文件格式，但如果在 Anki 开启时修改了文件、文件储存在网络驱动器上
或被 bug 损坏，集合仍有可能损坏。

当你运行工具菜单中的检查数据库时，如果 Anki 检测文件已损坏，将会收到一条消息。**恢复的最佳方法是从最
近的[自动备份](#备份)中恢复**，但如果你的备份太旧，可以尝试修复损坏。

在 Linux 上，确保安装了 sqlite3。在 Mac 上，它应该已经安装。在 Windows 上，下载
<http://www.sqlite.org/sqlite-3_6_23.zip>。

接下来，备份你的 collection.anki2 文件，以防下面的操作出现问题。

### Linux/macOS

打开终端，切换到集合所在的文件夹，并输入：

    sqlite3 collection.anki2 .dump > dump.txt

在文本编辑器中打开生成的 dump.txt 文件，查看最后一行。如果显示「rollback;」，将其更改为「commit;」。

然后在终端中运行以下命令：

    cat dump.txt | sqlite3 temp.file

确保使用 temp.file - 不要在右侧放置 collection.anki2，否则将覆盖文件。完成后，继续进行最后一步。

### Windows

将 `sqlite3.exe` 程序和你的牌组复制到桌面上。然后进入 **Start&gt;Run**，输入 `cmd.exe`。

如果你使用的是较新的 Windows，命令提示符可能不会在桌面上启动。如果在命令提示符中没有看到桌面，输入如
下内容，将 "administrator" 替换为你的登录名。

    cd C:\Users\Administrator\Desktop

然后输入：

    sqlite3 collection.anki2 .dump > dump.txt

在文本编辑器中打开生成的 dump.txt 文件，查看最后一行。如果显示「rollback;」，将其更改为「commit;」。

然后在终端中运行以下命令：

    type dump.txt | sqlite3 temp.file

确保使用 temp.file - 不要在右侧放置 collection.anki2，否则将覆盖文件。完成后，继续进行最后一步。

### 最后一步

检查是否没有收到错误信息，并且 temp.file 不是空的。此过程在优化集合过程中是正常的，因此新文件通常会
比旧文件小一些。

在确认文件不为空后：

- 将原始的 collection.anki2 文件重命名为其他名称

- 将 temp.file 重命名为 collection.anki2

- 将 collection.anki2 移回到你的集合文件夹中，覆盖旧版本

- 启动 Anki 并进入工具菜单中的检查数据库，以确保集合已成功恢复。
