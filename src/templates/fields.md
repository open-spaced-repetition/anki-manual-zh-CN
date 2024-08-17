# 字段替换

> 原
> 文：[Field Replacements - Anki Manual (ankiweb.net)](https://docs.ankiweb.net/templates/fields.html)

<!-- toc -->

## 基础替换

最基本的模板看起来是这样的：

    {{Front}}

当你把文本放在大括号内时，Anki 会寻找该名称对应的字段，并用字段的实际内容替换文本。

字段名称区分大小写。如果你有一个名为 `Front` 的字段，写成 `{{front}}` 是无法正常工作的。

你的模板不是仅限于列出字段。你还可以在模板中包含任意文本。例如，如果你在学习首都城市，并且你创建了一
个包含「国家」字段的笔记模板，你可能会创建一个前面这样的模板：

    What's the capital city of {{Country}}?

默认的背面模板会看起来是这样的：

    {{FrontSide}}

    <hr id=answer>

    {{Back}}

这意味着「先显示正面的文本，然后是一条分隔线，再然后是背面字段」。

'id=answer' 部分告诉 Anki 问题和答案之间的分隔线在哪里。这使得 Anki 在你按下「显示答案」时会自动滚动
到答案开始的位置（在移动设备的小屏幕上尤其有用）。如果你不希望在答案开头有水平线，你可以使用其他
HTML 元素，如段落或 div。

## 换行

卡片模板就像网页，这意味着需要一个特殊的命令才能创建换行。例如，如果你在模板中写下如下内容：

    one
    two

在预览中，你实际会看到：

    one two

要添加换行，你需要在行末添加 &lt;br&gt; 代码，如下所示：

    one<br>
    two

br 代码代表「(line) br(eak)」。

同样适用于字段。如果你想显示两个字段，每个字段在一行：

    {{Field 1}}<br>
    {{Field 2}}

## 单个字段的文字转语音

此功能需要 Anki 2.1.20、AnkiMobile 2.0.56 或 AnkiDroid 2.17。

要让 Anki 以美式英语发音朗读 Front 字段，你可以在卡片模板中这样写：

    {{tts en_US:Front}}

在 Windows、macOS 和 iOS 上，Anki 会使用操作系统自带的语音。在 Linux 上，默认没有语音，但可以通过安
装插件提供，例如[此插件](https://ankiweb.net/shared/info/391644525)。

若要查看所有可用语言/语音的列表，可以在卡片模板中放置以下内容：

    {{tts-voices:}}

如果有多种语音支持你选择的语言，你可以在列表中指定想要的语音，Anki 将选择第一个可用的语音。例如：

    {{tts ja_JP voices=Apple_Otoya,Microsoft_Haruka:Field}}

这样在 Apple 设备上使用 Otoya，在 Windows PC 上使用 Haruka。

在某些 TTS 实现中可以指定不同的速度：

    {{tts fr_FR speed=0.8:SomeField}}

速度和语音都是可选的，但必须包含语言。

在 Mac 上，你可以自定义可用的语音：

- 打开「系统设置」屏幕。

- 点击「辅助功能」。

- 点击「讲话」。

- 点击系统语音下拉菜单，选择「自定义」。

某些语音听起来会比其他更好，请试验以选择你喜欢的。需注意 Siri 语音仅能用于 Apple 应用程序。安装新语
音后，你需要重启 Anki 以便新语音可用。

在 Windows 上，有些像 Cortana 的语音无法选择，因为 Microsoft 不允许其他应用程序使用这些语音。

在完形填空笔记模板中，你可以使用 `cloze-only` 筛选器来让 Anki 只朗读隐藏部分，如下所示：

    {{tts en_US:cloze-only:Text}}

cloze-only 筛选器在 Anki 2.1.29+、AnkiMobile 2.0.65+ 及 AnkiDroid 2.17+ 上受支持。

## 对多个字段和静态文本的文字转语音

此功能需要 Anki 2.1.50+、AnkiMobile 2.0.84+ 或 AnkiDroid 2.17+。

如果你希望 TTS 朗读模板中包含的多个字段或静态文本，你可以这样使用：

```
[anki:tts lang=en_US] This text should be read. Here is {{Field1}} and {{Field2}}[/anki:tts]

This is other text on the template. It is outside of the tags so it should not be read.
```

## 特殊字段

你可以在模板中包含一些特殊字段：

    笔记的标签：{{Tags}}

    笔记的类型：{{Type}}

    卡片的牌组：{{Deck}}

    卡片的子牌组：{{Subdeck}}

    卡片的旗标：{{CardFlag}}

    卡片的模板（「正向」等）：{{Card}}

    前模板的内容（仅在背面模板中有效）：{{FrontSide}}

FrontSide 不会自动播放卡片正面的任何音频。如果你希望在卡片的正反两面自动播放相同音频，你需要手动在背
面也包含音频字段。

与其他字段一样，特殊字段名称区分大小写——例如，你必须使用 `{{Tags}}` 而不是 `{{tags}}`。

## 提示字段

可以在卡片的正面或背面添加一个字段，但默认情况下不会显示，除非你明确显示它。我们称之为「提示字段」。
在添加提示前，请记住在 Anki 中回答一个问题越容易，当你在现实中遇到它时，你记住该问题的可能性就越小。
请在继续之前阅读关于最低信息原则的文章： <https://super-memory.com/articles/20rules.htm>。

首先，如果还没有，你需要添加一个字段来存储提示。如果不确定如何操作，请查
看[字段](../editing.md#自定义字段)部分。

假设你创建了一个名为 MyField 的字段，你可以告诉 Anki 将其包含在卡片上但默认隐藏，通过在模板中添加以
下内容：

    {{hint:MyField}}

这将显示一个标记为「显示提示」的链接；当你点击它时，字段的内容将在卡片上显示。（如果 MyField 为空，
则不会显示任何内容。）

如果你在问题中显示提示，然后揭示答案，提示将再次隐藏。如果你希望在显示答案时总是显示提示，你需要从背
面模板中删除 `{{FrontSide}}` 并手动添加你希望出现的字段。

目前无法将提示字段用于音频——无论你是否点击提示链接，音频都会播放。

如果你希望自定义外观或行为，你需要自己实现提示字段。我们无法为此提供支持，但以下代码应可作为起步：

```
{{#Back}}
﻿<a class=hint href="#"
onclick="this.style.display='none';document.getElementById('hint4753594160').style.display='inline-block';return false;">
Show Back</a><div id="hint4753594160" class=hint style="display: none">{{Back}}</div>
{{/Back}}
```

## 字典链接

你还可以使用字段替换来创建字典链接。假设你正在学习一门语言，而你喜欢的在线字典允许你通过 URL 搜索文
本，例如：

    http://example.com/search?q=myword

你可以通过在模板中这样做来添加自动链接：

    {{Expression}}

    <a href="http://example.com/search?q={{Expression}}">在字典中查询</a>

上面的模板允许你在复习时通过单击链接来搜索每个笔记的表达。然而这里有一个问题，因此请查看下一部分。

## HTML 剥离

像模板一样，字段以 HTML 格式存储。在上面的字典链接示例中，如果表达中包含没有格式的单词「myword」，那
么 HTML 将是相同的：「myword」。但当你在字段中包含格式时，会包括额外的 HTML。如果「myword」被加粗，
实际的 HTML 将是「&lt;b&gt;myword&lt;/b&gt;」。

这可能会对字典链接等事情造成问题。在上面的示例中，字典链接最终会是：

    <a href="http://example.com/search?q=<b>myword</b>">在字典中查询</a>

链接中的额外字符可能会让字典网站感到困惑，从而可能无法匹配到任何内容。

为了解决这个问题，Anki 提供了在字段替换时剥离格式的能力。如果你在字段名称前加上 `text:`，Anki 将不包
括任何格式。因此，即使使用格式化文本，字典链接也可以正常工作：

    <a href="http://example.com/search?q={{text:Expression}}">在字典中查询</a>

## 从右到左文本

如果你使用的语言是从右到左书写的，你需要像这样调整模板：

    <div dir=rtl>{{FieldThatHasRTLTextInIt}}</div>

## 注音字符

某些语言通常在文本上方使用注解来显示字符的发音。这些注解称
为[注音字符](https://en.wikipedia.org/wiki/Ruby_character)。在日语中，这些称
为[假名](https://en.wikipedia.org/wiki/Furigana)。

在 Anki 中，你可以使用以下语法来显示注音字符：

    Text[Ruby]

假设上面的文本写在 MyField 中。默认情况下，如果你只是使用 `{{Myfield}}`，字段将以原样显示。要正确地
将注音字符放置在文本上方，请在模板中使用 `furigana` 筛选器，如下所示：

    {{furigana:MyField}}

以下是一些示例：

<!-- prettier-ignore -->
| 原始文本 | 渲染后文本 |
| --- | --- |
| `Text[Ruby]` | <ruby><rb>Text</rb><rt>Ruby</rt></ruby> |
| `日本語[にほんご]` | <ruby><rb>日本語</rb><rt>にほんご</rt></ruby> |
| `世[よ]の 中[なか]` | <ruby><rb>世</rb><rt>よ</rt></ruby>の<ruby><rb>中</rb><rt>なか</rt></ruby> |
| `世[よ]の中[なか]` | <ruby><rb>世</rb><rt>よ</rt></ruby><ruby><rb>の中</rb><rt>なか</rt></ruby> _(不正确!)_ |

注意第三个示例在「中」字符前有一个空格。这是为了指定注音文本只适用于该字符。如果没有空格，注音文本将
被错误地放置在「の」字符上，如第四个示例所示。

### 附加注音字符筛选器

除了 `furigana` 筛选器，你还可以只显示注音文本的某些部分，使用 `kana` 和 `kanji` 筛选器。`kana` 过滤
器只会显示注音文本，而 `kanji` 筛选器则完全去除注音文本。

<!-- prettier-ignore -->
| 原始文本 | 字段筛选器 | 渲染后文本 |
| --- | --- | --- |
| `日本語[にほんご]` | `{{furigana:MyField}}` | <ruby><rb>日本語</rb><rt>にほんご</rt></ruby> |
| `日本語[にほんご]` | `{{kana:MyField}}` | にほんご |
| `日本語[にほんご]` | `{{kanji:MyField}}` | 日本語 |

这些名称同样来源于日语。术语 [kana](https://en.wikipedia.org/wiki/Kana) 代表用于描述单词发音的音节系
统，而术语 [kanji](https://en.wikipedia.org/wiki/Kanji) 代表其汉字。

## 媒体和 LaTeX

Anki 不会扫描模板中的媒体引用，因为这样做很慢。这对在模板中包含媒体有一定影响。

### 静态声音/图像

如果你希望在卡片中包含在每张卡片上相同的图像或声音（例如，公司徽标在每张卡片顶部）：

1. 重命名文件，使其以下划线开头，例如 "\_logo.jpg"。下划线告诉 Anki 该文件被模板使用，并在共享牌组时
   导出。

2. 在你的正面或背面模板中添加对媒体的引用，如下：

<img src="_logo.jpg">

### 字段引用

对字段的媒体引用不受支持。它们在复习期间可能显示，也可能不显示，并且在检查未使用的媒体、导入/导出等
操作中将无法正常工作。无法正常工作的示例：

    <img src="{{Expression}}.jpg">

    [sound:{{Word}}]

    [latex]{{Field 1}}[/latex]

相反，你应该在字段中包含媒体引用。请查看[导入部分](../importing/text-files.md#导入媒体)以获取更多信
息。

## 检查你的答案

你可以在 [YouTube](http://www.youtube.com/watch?v=5tYObQ3ocrw&yt:cc=on) 上观看关于此功能的视频。

检查答案的最简单方法是在卡片添加屏幕的左上角单击「Basic」，然后选择「Basic (type in the answer)」。
如果你已经下载了一个共享牌组，并希望在其中输入答案，你可以修改它的卡片模板。如果它有一个模板像这样：

    {{Native Word}}

    {{FrontSide}}

    <hr id=answer>

    {{Foreign Word}}

要输入外语单词并检查是否正确，你需要编辑前面的模板，使其看起来像这样：

    {{Native Word}}
    {{type:Foreign Word}}

注意，我们在想要比较的字段前添加了 `type:`。由于 FrontSide 在卡片的背面，输入答案框也会出现在背面。

在复习时，Anki 会显示一个文本框，你可以在其中输入答案，按下 <kbd>Enter</kbd> 键或者显示答案后，Anki
会向你显示哪里正确，哪里错误。文本框的字体大小将是你为那个字段配置的大小（通过编辑时的「Fields」按
钮）。

这个功能不会改变卡片的答题方式，所以你还是要决定自己记得好不好。

一张卡片只能使用一个输入比较。如果多次添加上述文本，将无效。它也只支持单行，因此不适用于比较包含多行
的字段。

Anki 使用等宽字体进行答案比较，以便「已提供」和「正确」部分对齐。如果你希望为答案比较覆盖字体，你可
以在样式部分的底部放置以下内容：

```css
code#typeans {
  font-family: "myfontname";
}
```

这将影响以下用于答案比较的 HTML：

```html
<code id="typeans">...</code>
```

高级用户可以使用 css 类 `typeGood`、`typeBad` 和 `typeMissed` 覆盖默认的输入答案颜色。AnkiMobile支持
`typeGood` 和 `typeBad`，但不支持 `typeMissed`。

如果希望覆盖输入框的大小而不想在「Fields」对话框中更改字体，可以使用 `!important` 来覆盖默认的内联样
式，如下所示：

```css
#typeans {
  font-size: 50px !important;
}
```

还可以为填空删除卡片输入答案。为此，请在前后模板中添加 `{{type:cloze:Text}}`，这样背面看起来像这样：

    {{cloze:Text}}
    {{type:cloze:Text}}
    {{Extra}}

注意，由于填空类型不使用 FrontSide，这必须添加到填空笔记模板的两边。

如果有多个部分被省略，你可以在文本框中用逗号分隔答案。

在浏览器中的「[预览」对话框](intro.md)中不会显示输入答案框。当你复习或在卡片类型窗口中查看预览时，它
们将显示。

在 [ankiweb.net](../syncing.md) 上复习卡片时，不会显示输入答案框。
