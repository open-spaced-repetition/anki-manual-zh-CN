# 学习

<!-- toc -->

当你找到了一个喜欢的牌组或者输入了一些笔记后，就可以开始学习了。

## 牌组

在 Anki 中，学习仅限于当前选择的牌组以及其包含的任何子牌组内。

在牌组屏幕上，你的牌组和子牌组会以列表形式显
示。[今天的新卡片、学习中的卡片和待复习的卡片](getting-started.md#卡片类型) 也会在这里显示。

![牌组屏幕](media/decks_screen.png)

当你点击一个牌组时，它会成为「当前牌组」，Anki 会切换到学习屏幕。你可以随时通过点击主窗口顶部的「牌
组」返回牌组列表。（你也可以使用菜单中的「学习牌组」操作从键盘选择一个新的牌组，或者可以按下
<kbd>s</kbd> 键来学习当前选择的牌组。）

你可以点击牌组右侧的齿轮按钮来重命名或删除牌组，改变其[选项](deck-options.md)，
或[导出](exporting.md)它。

## 学习概览

点击一个牌组进行学习后，你会看到一个显示今天到期卡片数的屏幕。这称为「牌组概览」屏幕：

![学习概览](media/study_overview.png)

卡片分为[三种类型](getting-started.md#卡片类型)：新卡、学习中和待复习。如果你在牌组选项中激活
了[搁置关联卡](#关联卡与搁置)，你可能会看到有多少卡片将被灰色显示搁置：

![学习概览 (被搁置的卡片)](media/study_overview_buried_cards.png)

要开始一次学习会话，点击**开始学习**按钮。Anki 将继续为你展示卡片，直到当天要展示的卡片全部展示完为
止。

在学习期间，你可以按下键盘上的 <kbd>s</kbd> 键返回概览。

## 问题

当一张卡片展示时，最初只会展示问题。在思考答案后，点击**显示答案**按钮，或者按下空格键。然后会显示答
案。如果你花了一些时间回忆答案，这是可以的，但作为一个一般规则，如果你在大约 10 秒内无法回答，可能最
好移动并显示答案而不是继续苦思冥想。

当显示答案时，你应该将你想到的答案与显示的答案进行比较，并告诉 Anki 你记忆得有多好。如果你不相信自己
能准确地比较你的答案，可以让 Anki [提示你输入答案](templates/fields.md#检查你的答案)而不是仅仅显示答
案给你。

## 学习/重学卡片

在学习新卡，或重学你已忘记的卡片时，Anki 会一遍或多遍地展示这些卡片以帮助你记忆。每次展示称为「学习
步骤」。默认情况下，有两个步骤：1 分钟和 10 分钟。你可以在[牌组选项](deck-options.md#新卡片)中更改步
骤数和它们之间的间隔。

当在学习时，有四个评级按钮：

- **重来**会将卡片移回到第一步。

- **困难**会重复当前步骤。

  - 如果卡片处在第一步（并且是唯一的一步），延迟是步骤的 50% 以上。但此延迟最多比步骤多一天。
  - 如果卡片处在第一步并且你设置了多于一步的步骤，延迟将是重来和良好的平均值，即第一、第二步的平均
    值。
  - 如果卡片处在后续步骤中，困难会重复之前的延迟。

- **良好**会将卡片移至[下一步](deck-options.md#初学间隔)。如果卡片处在最后一步，卡片将被转换为复习卡
  片（它完成「毕业」）。默认情况下，一旦卡片达到学习步骤的结束，卡片将在第二天再次展示，然后在越来越
  长的延迟后再次展示（见下一节）。

- **简单**立即将卡片转换为复习卡片，即使还有步骤剩余。[默认](deck-options.md#简单间隔)情况下，卡片将
  在 4 天后再次展示，然后在越来越长的延迟后再次展示。在 v1 调度器中，如果在重学模式下，则不会显示
  「简单」按钮，因为它会给出和「良好」一样的间隔。在
  [v2 调度器+](https://faqs.ankiweb.net/the-anki-2.1-scheduler.html) 中，当卡片处于重学时，「简单」
  按钮会使间隔增加 1 天。

当卡片第一次出现时，它们从第一步开始。这意味着第一次在卡片上回答**良好**时，将在 10 分钟后再显示一
次，并且会跳过初始的 1 分钟步骤。但如果你按下**重来**，卡片将在 1 分钟后出现。

你可以使用键盘上的 <kbd>1</kbd>, <kbd>2</kbd>, <kbd>3</kbd> 和 <kbd>4</kbd> 键来选择特定的按钮，其中
<kbd>1</kbd> 是 **重来**。按下 <kbd>Space</kbd> 或 <kbd>Enter</kbd> 将选择**良好**。

如果没有其他卡片可以展示，Anki 会再次展示学习卡片，即便它们的延迟还没完全屏蔽。如果你更愿意等待完整
的学习延迟，可以在[Preferences>Scheduling>Learn Ahead Limit](preferences.md) 中更改此行为。

## 复习卡片

当卡片以前学过并准备再次复习时，有四个按钮可以对你的答案进行评级：

- **重来**将你的答案标记为不正确，并要求 Anki 在未来更频繁地展示该卡片。卡片被称为「遗忘」。请参
  见[遗忘](deck-options.md#遗忘)部分以获取有关如何处理遗忘复习的更多信息。

- **困难**默认情况下，比上次以稍长的延迟展示卡片，并要求 Anki 在未来更频繁地展示卡片。

- **良好**告诉 Anki 上次的延迟大约合适，卡片难度不需要调低或调高。
  在[默认起始难度](deck-options.md#初始简易度)下，卡片将在上一次大约 2.5 倍的时间后再次展示，因此如
  果你上次等待了 10 天才看到该卡片，则下次的延迟约为 25 天。

- **简单**告诉 Anki 延迟太短。卡片安排会比「良好」更
  久，[并且 Anki 将在未来更少地安排该卡片。](deck-options.md#简单复习间隔乘数) 因为「简单」迅速增加
  了延迟，最好只用于最简单的卡片。通常你应该发现自己在回答「良好」。

如同学习卡片一样，你可以使用键盘上的 <kbd>1</kbd>, <kbd>2</kbd>, <kbd>3</kbd> 和 <kbd>4</kbd> 来选择
答案。按下 <kbd>空格键</kbd> 或 <kbd>Enter</kbd> 将选择 **良好**。

参见[牌组选项](deck-options.md)和
[FAQ](https://faqs.ankiweb.net/what-spaced-repetition-algorithm.html) 以了解更多关于算法如何工作的知
识。

## 到期计数

当只有问题展示时，Anki 在屏幕底部显示三个数字，如 6 + 9 + 59。它们代表新卡片（蓝色）、学习中的卡片
（红色）和待复习的卡片（绿色）。如果你不想看到这些数字，可以在 Anki 的[首选项](preferences.md)中关闭
它们。

![到期计数](media/due_counts.png)

在 v1 调度器中，这些数字表示完成该队列中所有卡片所需的*复习*数，而非*卡片*数。如果你为失效卡片配置了
多个步骤，数字将在你失败一个卡片时增长超过一个，因为那张卡片需要被多次展示。

从 [v2 调度器](https://faqs.ankiweb.net/the-anki-2.1-scheduler.html)开始，这些数字表示**卡片**，所以
无论剩下多少步骤，数字总是只会增加一个。

当答案显示时，Anki 在每个按钮上方显示卡片下次展示时间的预测值。如果你更喜欢不看预测值，可以在 Anki
的[首选项](preferences.md)中禁用它们。

## 模糊系数

当你在复习卡片上选择一个难度按钮时，Anki 也会应用少量的随机「模糊」以防止同时引入并被赋予相同评级的
卡片黏在一起，总是在同一天进行复习。这种模糊将
在[v3 调度器](https://faqs.ankiweb.net/the-2021-scheduler.html)启用时显示在答案按钮上，所以如果你使
用较早的版本并注意到你选择的内容与卡片实际间隔之间有些许差异，这可能是原因。

学习卡片也会有最多 5 分钟的额外延迟，以使它们不总是同样顺序出现，但答案按钮不会反映这一点。无法关闭
此功能。

## 编辑及更多

你可以点击左下角的**编辑**按钮来编辑当前笔记。完成编辑后，你将返回学习。编辑屏幕的工作方式
与[添加笔记](editing.md)屏幕非常相似。

在复习屏幕的右下角有一个标注为**更多**的按钮。此按钮提供了一些对当前卡片或笔记的操作：

- [**旗标卡片**](editing.md#使用旗标)：为卡片添加一个彩色旗标，或者关闭它。旗标将在学习期间出现，你
  可以在浏览屏幕中搜索标记的卡片。当你想在稍后对卡片执行某些操作时，这很有用，比如回家后查单词。如果
  你使用的是 Anki 2.1.45+，也可以从[浏览器中](browsing.md)重命名标记。

- **搁置卡片 / 笔记**：搁置卡片或该笔记的所有卡片直到第二天。（如果你想在之前取消搁置，可以点
  击[牌组概览](studying.md#学习概览)屏幕上的「取消搁置」按钮。）这在你目前无法回答卡片或想在其他时间
  重新考虑它们时很有用。搁置也可以[自动发生](studying.md关联卡与搁置)在同一笔记的卡片。

旧调度器中，如果卡片处于学习中被搁置，它们会在被搁置前移动回到新卡或复习卡队列。

然而，使用[2.1 调度器](https://faqs.ankiweb.net/the-anki-2.1-scheduler.html)，搁置卡片并不会重置卡片
的学习步骤。

- **重置卡片**：将当前卡片移至[新卡队列的末尾](browsing.md#卡片)。

从 Anki 2.1.50+ 开始，Anki 会记住新卡第一次学习时的原始顺序，当使用 v3 调度器时。「恢复初始位置」选
项允许你在遗忘卡片时将卡片重置回到原来的位置。

启用时，「复习和遗忘次数归零」选项将把卡片的复习和遗忘次数重置为零。它不会删除卡片信息屏幕底部显示的
复习历史。

- **设置到期日**：将卡片放入复习队列，并[使其在特定日期到期。](browsing.md#卡片)

- **暂停卡片 / 笔记**：暂停卡片或该笔记的所有卡片，直到它们被手动解除暂停（通过在浏览器中点击暂停按
  钮）。如果你想在一段时间内避免复习该笔记而不是删除它，这很有用。旧调度器中，如果卡片处于学习中被暂
  停，它们会在被暂停前移动回到新卡或复习队列。

然而，使用[2.1 调度器](https://faqs.ankiweb.net/the-anki-2.1-scheduler.html)，暂停卡片并不会重置卡片
的学习步骤。

- **选项**：编辑当前牌组的[选项](deck-options.md)。

- **卡片信息**：显示关于卡片的[统计信息](stats.md#卡片信息)。

- **上一张卡片信息**：显示关于上一张卡片的[统计信息](stats.md#卡片信息)。

- [**标记笔记**](editing.md#标记标签)：为当前笔记添加“标记”标签，方便在浏览器中找到。这类似于标记单
  个卡片，但使用标签代替。因此，如果笔记有多张卡片，所有卡片在搜索标记标签时都会出现。大多数用户倾向
  于使用标记功能。

- **创建副本**：在编辑器中打开当前笔记的一个[重复项](browsing.md#查找重复)，可以稍作修改以轻松获取卡
  片的变体。默认情况下，重复的卡片将创建在与原始卡片相同的牌组中。

- **删除笔记**：删除笔记及其所有卡片。

- **重播音频**：如果卡片正面或背面有音频，则重播。

- **暂停音频**：如果音频正在播放，暂停它。

- **音频快退 5 秒 / 快进 5 秒**：向后 / 向前跳跃当前播放音频 5 秒。

- **录制自己的声音**：通过麦克风录音以检查自己的发音。此录音是临时的，当你移动到下张卡片时将消失。如
  果想要永远添加音频到卡片中，可以在编辑窗口中进行。

- **重播自己的声音**：重播你自己声音的上一段录音（可能是在显示答案后）。

## 显示顺序

学习将显示来自所选牌组及其包含的任何牌组的卡片。因此，如果你选择你的「法语」牌组，子牌组
「French::Vocab」和「French::My Textbook::Lesson 1」也会显示。

Anki 从牌组中获取卡片的方式取决于使用的算法：

- 使用 v1 调度器时，当一个牌组有子牌组时，卡片会[轮流](studying.md#显示顺序)出现在每个牌组中。

- 使用 [v2 调度器](https://faqs.ankiweb.net/the-anki-2.1-scheduler.html)时，当一个牌组有子牌组时，复
  习内容同时从所有子牌组中抽取。子牌组的复习限制被忽略 - 仅适用于你点击的牌组的限制。

- 使用 [v3 调度器](https://faqs.ankiweb.net/the-2021-scheduler.html)时，每个子牌组的限制也被执行，你
  不需要按牌组顺序查看卡片。有关详细信息，请参见手册中
  的[牌组选项](deck-options.md#复习卡片排列顺序)部分。

默认情况下，对于新卡片，Anki 按字母顺序从牌组中获取卡片。因此，在上述示例中，你将首先从「French」中
获取卡片，然后是「My Textbook」，最后是「Vocab」。你可以利用这一点来控制卡片显示的顺序，将优先级高的
卡片放置在列表中较高的牌组中。当计算机按字母顺序对文本进行排序时，“-”字符位于字母字符之前，“\~”位于
之后。因此，你可以将牌组称为「-Vocab」以使其首先出现，并将另一牌组称为「\~My Textbook」以使其在所有
其他内容之后出现。

新卡片和复习卡片是分开抽取的，Anki 在继续到下一个牌组之前不会等待两个队列都为空，因此可能会在看到一
个牌组的复习时接触到另一个牌组的新卡片，反之亦然。如果不想这样，直接点击想要学习的牌组而不是父牌组之
一。

由于学习中的卡片在时间上比较紧迫，它们会从所有牌组中一次性提取，并按到期顺序显示。

要控制给定牌组中复习显示的顺序，或将新卡片从有序更改为随机顺序，请参见[牌组选项](deck-options.md)。
对于新卡片的更细粒度排序，你可以在[浏览](browsing.md)中更改顺序。

## 关联卡与搁置

回顾[基础知识](getting-started.md)，Anki 可以为你输入的每个项创建多张卡片，例如正面→背面卡片和背面→
正面卡片，或者从同一文本中两种不同的完形填空。这些相关的卡片称为「同类卡片」。

当你回答一张有同类卡片的卡片时，Anki 可以通过自动「搁置」它们防止这些卡片在同一个会话中显示。搁置的
卡片在时钟转到新的一天之前或你手动通过「取消搁置」按钮（可见于[牌组概览](studying.md#学习概览)屏幕底
部）取消搁置之前将不会显示。即使同类卡片不在同一牌组中，Anki 也会搁置它们（例如，如果你使用
了[覆盖牌组](templates/intro.md)功能）。

你可以在[牌组选项](deck-options.md)屏幕中启用搁置 - 新卡片和复习卡片有独立的设置。

Anki 只会搁置新卡片或复习卡片的同类卡片，不会搁置正在学习中的卡片，因为对这些卡片来说，时间至关重
要。另一方面，当你学习一张正在学习中的卡片时，任何新的/复习中的同类卡片都会被搁置。

请注意，从[v2 调度器](https://faqs.ankiweb.net/the-anki-2.1-scheduler.html)开始，Anki 现在区分手动搁
置和自动搁置的卡片，以便你可以取消搁置一组而不影响另一组。

还要注意，一张卡片不能同时被搁置和暂停。暂停被搁置的卡片会取消搁置它。搁置已暂停的卡片在 Anki
2.1.49+ 上不起作用，而在早期版本中，它会取消暂停卡片。

## 快捷键

Anki 中的大多数常见操作都有快捷键。它们中的大多数可以在界面中找到：菜单项在其旁边列出了快捷键，将鼠
标光标悬停在某个按钮上通常会在工具提示中显示其快捷键。

学习时，<kbd>Space</kbd> 或 <kbd>Enter</kbd> 可以显示答案。当答案显示时，可以使用 <kbd>Space</kbd>
或 <kbd>Enter</kbd> 选择「好」按钮。你可以使用 <kbd>1</kbd>-<kbd>4</kbd> 键选择特定的易度按钮。许多
人发现，用 <kbd>Space</kbd> 回答大多数卡片，然后将一根手指放在 <kbd>1</kbd> 上，以备遗忘时使用很方
便。

工具菜单中的「学习牌组」项可以让你快速通过键盘切换到某个牌组。可以使用“/”键触发它。打开时，它将显示
你所有的牌组，并在顶部显示一个过滤区域。输入字符时，Anki 会仅显示与你输入的字符匹配的牌组。可以添加
空格以分隔多个搜索词，Anki 将仅显示匹配所有词的牌组。因此，“ja 1”或“on1 ja”将匹配名为
「Japanese::Lesson1」的牌组。

## 落后

如果在复习中落后，Anki 会优先处理等待时间最长的卡片。它这样做是通过取等待时间最长的卡片，并以随机顺
序将它们显示给你，直到达到你的每日复习限制。这种排序确保没有卡片会无限期等待，但这意味着如果引入新卡
片，它们的复习不会出现，直到你已处理完积压的卡片。

如果希望更改过期复习的顺序，可以通过创建一个[筛选牌组](filtered-decks.md)实现。

当你回答长期等待的卡片时，Anki 会在确定下一次应该显示该卡片的时间点时考虑到这种延迟。更多信息请参见
Anki 的间隔重复[算法](https://faqs.ankiweb.net/due-times-after-a-break.html)部分。