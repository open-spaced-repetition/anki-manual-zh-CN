# 样式与 HTML

<!-- toc -->

## 卡片样式

你可以在 YouTube 上观看 [关于卡片样式的视频](http://www.youtube.com/watch?v=F1j1Zx0mXME&yt:cc=on)。
视频展示的是 Anki 2.0 的界面，但其概念大体相同。

可以通过单击「样式」按钮来访问卡片屏幕的样式部分，该按钮位于「背面模板」按钮旁边。在该部分，你可以更
改卡片的背景颜色、默认字体、文本对齐方式等。

你可以使用的标准选项有：

**font-family**\
在卡片上使用的字体名称。如果你的字体中有空格，如「MS Unicode」，那么你需要用双引号将字体名称括起来，
就像本句中的示例一样。还可以在一张卡片上使用多个字体；有关详细信息，请参见下文。

**font-size**\
字体的像素大小。更改时，请确保在末尾保留 px。

**text-align**\
文本应对齐在中心、左侧或右侧。

**color**\
文字的颜色。像『blue』、『lightyellow』等简单的颜色名称将有效，或你可以使用 HTML 颜色代码来选择任意
颜色。更多信息请参见[此网页](https://htmlcolorcodes.com/)。

**background-color**\
卡片背景的颜色。

任何 CSS 都可以放置在样式部分 - 高级用户可能希望做一些例如添加背景图片或渐变的操作。如果你想知道如何
实现某种特定的格式，请在网上搜索有关如何在 CSS 中实现它的信息，因为有大量的文档可用。

样式在所有卡片间共享，这意味着当你进行调整时，它将影响该笔记类型的所有卡片。不过，也可以指定特定卡片
的样式。以下示例将在所有卡片上使用黄色背景，除了第一个卡片：

```css
.card {
  background-color: yellow;
}
.card1 {
  background-color: blue;
}
```

## 图片调整大小

Anki 默认会缩小图像以适应屏幕。你可以通过添加以下内容来更改此行为，把它放在样式部分的底部（在默认的
`.card { ... }` 之外）：

```css
img {
  max-width: none;
  max-height: none;
}
```

AnkiDroid 有时
在[调整图像以适应屏幕时遇到麻烦](https://github.com/ankidroid/Anki-Android/issues/3612)。使用 css 设
置最大图像尺寸应该可以解决这个问题，但在 AnkiDroid 2.9 中似乎被忽略了。一个解决方法是将 `!important`
附加到每个样式指令，例如：

```css
img {
  max-width: 300px !important;
  max-height: 300px !important;
}
```

如果你尝试更改图像的样式并发现标记卡片时出现的星星受到影响（例如，它变得过大），你可以使用以下内容针
对它：

```css
img#star {
...;
}
```

你可以通过使用 Chrome 交互式地探索卡片的样式：

<https://addon-docs.ankiweb.net/porting2.0.html#webview-changes>

Anki 2.1.50+ 原生支持在编辑器中调整图像大小。

## 字段样式

默认样式适用于整个卡片。你还可以使某些字段或卡片的某部分使用不同的字体、颜色等。这在学习外语时尤其重
要，因为 Anki 有时无法正确显示字符，除非选择了合适的字体。

假设你有一个「Expression」字段，你想给它设置 OSX 泰语字体「Ayuthaya」。假设你的模板已经显示：

What is {{Expression}}?

{{Notes}}

我们需要做的是在我们想要设置样式的文本前后加上一些 HTML。我们将在文本前放置以下内容：

<div class=mystyle1>

然后在其后放置以下内容：

</div>

通过像上面那样包裹文本，我们告诉 Anki 用我们稍后要创建的自定义样式「mystyle1」设置包裹的文本样式。

因此，如果我们希望整个「What is …​?」表达式使用泰语字体，我们会使用：

<div class=mystyle1>What is {{Expression}}?</div>

{{Notes}}

如果我们只希望表达式字段本身使用泰语字体，我们将使用：

What is <div class=mystyle1>{{Expression}}</div>?

{{Notes}}

编辑模板后，我们现在需要转到模板之间的样式部分。在编辑之前，它看起来应该像这样：

```css
.card {
  font-family: arial;
  font-size: 20px;
  text-align: center;
  color: black;
  background-color: white;
}
```

将你的新样式添加到底部，使其看起来像这样：

```css
.card {
  font-family: arial;
  font-size: 20px;
  text-align: center;
  color: black;
  background-color: white;
}

.mystyle1 {
  font-family: ayuthaya;
}
```

你可以在样式中包含任何你想要的样式。如果你还想增加字体大小，你可以将 mystyle1 部分更改为：

```css
.mystyle1 {
  font-family: ayuthaya;
  font-size: 30px;
}
```

也可以将自定义字体与牌组打包，这样你就不需要在计算机或移动设备上安装它们。有关更多信息，请参
阅[安装字体](#installing-fonts)部分。

## 音频重播按钮

当音频或文字转语音包含在你的卡片上时，Anki 会显示可点击的按钮以重播音频。

如果你不希望看到这些按钮，可以在首选项屏幕中隐藏它们。

你可以在你的卡片样式中自定义它们的外观，例如，将其变小并变色，你可以使用以下内容：

```css
.replay-button svg {
  width: 20px;
  height: 20px;
}
.replay-button svg circle {
  fill: blue;
}
.replay-button svg path {
  stroke: white;
  fill: green;
}
```

## 文本方向

如果你使用书写方向从右到左的语言，例如阿拉伯语或希伯来语，你可以在.card部分中添加 CSS 的 `direction`
属性以便在复习时正确显示：

```css
.card {
  direction: rtl;
}
```

这会改变整个卡片的方向。你可以通过在一些 HTML 中包装字段参考来仅更改某些字段的方向：

<div dir="rtl">{{Front}}</div>

要在编辑器中更改字段的方向，请参阅 [编辑](../editing.md#customizing-fields)部分。

## 其他 HTML

你的模板可以包含任意 HTML，这意味着所有用于互联网网页的布局可能性也可以用于你的卡片。例如，通过使用
表格，你可以更改布局，使卡片的正面和背面显示在左侧和右侧，而不是顶部和底部。

覆盖 HTML 的所有功能超出了本手册的范围，但如果你想了解更多，有很多不错的 HTML 入门指南可以在网上找
到。

## 浏览器外观

如果你的卡片模板很复杂，可能难以阅读问题和答案列（称为「正面」和「背面」）在
[卡片列表](../browsing.md#cardnote-table)中。「浏览器外观」选项允许你定义一个仅在浏览器中使用的自定
义模板，以便你可以仅包括重要字段，并根据需要更改顺序。语法与标准卡片模板相同。

使用此选项时，如果问题列中的文本在答案列的开始处重复，Anki 只会在问题列中显示文本。例如，如果问题列
文本是「People in Ladakh speak」，而答案是「People in Ladakh speak Ladakhi」，答案列将仅显示
「Ladakhi」，省略其余部分。

## 平台特定 CSS

Anki 定义了一些特殊的 CSS 类，允许你为不同的平台定义不同的样式。下面的示例显示了如何根据你所在的平台
更改字体：

```css
/* Windows */
.win .example {
  font-family: "Example1";
}
/* macOS */
.mac .example {
  font-family: "Example2";
}
/* Linux 桌面 */
.linux:not(.android) .example {
  font-family: "Example3";
}
/* Linux 桌面和 Android 设备 */
.linux .example {
  font-family: "Example4";
}
/* Android 和 iOS */
.mobile .example {
  font-family: "Example5";
}
/* iOS */
.iphone .example,
.ipad .example {
  font-family: "Example6";
}
/* Android */
.android .example {
  font-family: "Example7";
}
```

在模板中：

```html
<div class="example">{{Field}}</div>
```

你也可以使用属性像 .gecko、.opera 和 .ie 来选择在 AnkiWeb 上使用的特定浏览器。详细选项请参阅
<http://rafael.adm.br/css_browser_selector/>。

## 安装字体

如果你在工作或学校计算机上使用 Anki，或在没有权限安装新字体的情况下，或者在移动设备上使用 Anki，可以
直接将字体添加到 Anki。

要将字体添加到 Anki，必须是 TrueType 格式。TrueType 字体的文件名以 .ttf 结尾，例如「Arial.ttf」。找
到 TrueType 字体后，我们需要将其添加到媒体文件夹中：

1. 重命名文件，在开头添加下划线，使其变为类似「\_arial.ttf」。添加下划线会告知 Anki 这个文件将用于模
   板，在检查未使用的媒体时不会删除。

2. 在计算机的文件浏览器中，转到你的 [Anki 文件夹](../files.md)，然后打开名为「User 1」的文件夹（如果
   你重命名或添加配置文件，则为你的配置文件名）

3. 在该文件夹中，你应该看到一个名为 collection.media 的文件夹。将重命名的文件拖动到该文件夹。

之后，我们需要更新模板：

1. 点击主屏幕顶部的 **添加**，然后使用左上角的按钮选择要更改的笔记类型。

2. 点击 **卡片**。

3. 在样式部分，添加以下文本到底部（在最后一个「}」字符之后），用你复制到媒体文件夹中的文件名替换
   「\_arial.ttf」：

```css
@font-face {
  font-family: myfont;
  src: url("_arial.ttf");
}
```

仅更改「arial」部分，不要更改「myfont」部分。

之后，你可以选择更改整个卡片的字体，或仅更改某个字段的字体。要更改整个卡片的字体，只需在 .card 部分
找到 font-family: 行并将字体更改为「myfont」。要仅更改特定字段的字体，请参阅上面
的[字段样式](#field-styling)说明。

请确保文件名完全匹配。如果文件叫做 arial.TTF 而你在卡片模板中写的是 arial.ttf，它将无法工作。

## 夜间模式

你可以自定义在首选项屏幕中启用夜间模式时模板的外观。

如果你希望更轻的灰色背景，你可以使用类似以下的样子：

```css
.card.nightMode {
  background-color: #555;
}
```

如果你有一个 'myclass' 样式，以下内容将在启用夜间模式时以黄色显示文本：

```css
.nightMode .myclass {
  color: yellow;
}
```

## 淡入和滚动

Anki 默认会自动滚动到答案。它会查找 id=answer 的 HTML 元素，并滚动到该位置。你可以将 id 放在其他元素
上以调整滚动位置，或删除 id=answer 来关闭滚动。

卡片的正面默认淡入显示。如果你希望调整此延迟，可以在你的正面卡片模板顶部放置以下内容：

```html
<script>
  qFade = 100;
  if (typeof anki !== "undefined") anki.qFade = qFade;
</script>
```

100（毫秒）是默认值；设置为 0 可禁用淡入。

## Javascript

由于 Anki 卡片被视为网页，因此可以通过卡片模板在你的卡片上嵌入一些 Javascript。有关良好的参考，请阅
读[此帖子](https://forums.ankiweb.net/t/card-templates-user-input-101-buttons-keyboard-shortcuts-etc-guide/13756)
在论坛上的帖子。

由于 Javascript 是一项高级功能，而且可能出现许多问题， **Javascript 功能不提供任何支持或保修**。我们
无法提供任何关于编写 Javascript 的帮助，并且无法保证你编写的任何代码在未来的 Anki 更新中无需修改仍能
继续工作。如果你无法自行解决所遇到的任何问题，请避免使用 Javascript。每个 Anki 客户端可能会以不同的
方式实现卡片显示，因此你需要在各个平台上测试这种行为。一些客户端是通过保持一个长时间运行的网页，并在
卡片被复习时动态更新其部分内容来实现的，因此你的 Javascript 需要使用类似 document.getElementById()
的方式来更新文档的各个部分，而不是使用 document.write() 这样的方式。

像 window.alert 这样的函数可能不可用。Anki 会将 javascript 错误写入终端，因此你需
要[查看控制台](https://addon-docs.ankiweb.net/console-output.html#console-output)来查看它们。要调试
JavaScript 的相关问题，你可以使用 Chrome
的[检查器](https://addon-docs.ankiweb.net/debugging.html#webviews)。
