- [MarkDown语法](#markdown语法)
  - [一、Markdown纯文本基本语法](#一markdown纯文本基本语法)
    - [1.标题](#1标题)
- [This is an H1](#this-is-an-h1)
  - [This is an H2](#this-is-an-h2)
- [this is H1](#this-is-h1)
  - [this is H2](#this-is-h2)
          - [this is H6](#this-is-h6)
    - [2.字体](#2字体)
    - [3. 分割线](#3-分割线)
    - [4. 引用](#4-引用)
    - [5. 列表](#5-列表)
    - [6. 表格](#6-表格)
    - [7. 代码](#7-代码)
    - [8. 段落和换行](#8-段落和换行)
  - [二、Markdown纯文本进阶语法](#二markdown纯文本进阶语法)
    - [1. 更改字体、大小、颜色](#1-更改字体大小颜色)
    - [2. 为文字添加背景色](#2-为文字添加背景色)
    - [3. 设置文字居中](#3-设置文字居中)
    - [4. 加入上下标](#4-加入上下标)
  - [三、Markdown进阶使用](#三markdown进阶使用)
    - [1. 超链接](#1-超链接)
    - [2. 自动链接](#2-自动链接)
    - [3. 插入图片](#3-插入图片)
      - [1. 将本地图片上传到github](#1-将本地图片上传到github)
      - [2. 把图片存入markdown文件](#2-把图片存入markdown文件)
    - [4. 调整图片格式](#4-调整图片格式)
    - [5. LaTeX 公式](#5-latex-公式)
    - [6. 内容目录](#6-内容目录)
# MarkDown语法

## 一、Markdown纯文本基本语法
### 1.标题
Markdown 支持两种标题的语法，类 Setext 和类 atx 形式。 类 Setext 形式是用底线的形式，利用 = （最高阶标题）和 - （第二阶标题）

This is an H1
=======

This is an H2
----------

任何数量的 = 和 - 都可以有效果。

这里需要注意一点，由于分割线也是 “----”， 因此在使用分割线时，一定要空一行，不然会把上方的文字识别为第二阶标题。原因会在后面的段落和换行中说到。
类 Atx 形式则是在行首插入 1 到 6 个 # ，对应到标题 1 到 6 阶，例如：

# this is H1
## this is H2
###### this is H6
效果不再展示，但要注意的是，标准语法一般在 # 后跟个空格再写文字，不然可能会无法识别。

### 2.字体
Markdown 使用星号（*）和底线（_）作为标记强调字词的符号，你可以随便用你喜欢的样式，唯一的限制是，你用什么符号开启标签，就要用什么符号结束。但个人感觉写中文时还是（*）比较好用，因为它不区分全角半角，不用切换输入法。 示例：

**这是加粗**
__这也是加粗__
*这是倾斜*
_这也是倾斜_
***这是加粗倾斜***
~~这是加删除线~~
效果如下： 这是加粗 这也是加粗 这是倾斜 这也是倾斜 这是加粗倾斜 ~~这是加删除线~~

注意：强调也可以直接插在文字中间，但是如果你的 * 和 _ 两边都有空白的话，它们就只会被当成普通的符号。 如果要在文字前后直接插入普通的星号或底线，你可以用反斜线 \ 。

### 3. 分割线
你可以在一行中用三个以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西。你也可以在星号或是减号中间插入空格。下面每种写法都可以建立分隔线：

* * *
***
**********
- - -
_________________

### 4. 引用
在引用的文字前加 > 即可。 在 Markdown 文件中建立一个区块引用，那会看起来像是你自己先断好行，然后在每行的最前面加上 > ：

> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
> consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
> Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
> 
> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
> id sem consectetuer libero luctus adipiscing.
效果如下：

This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse id sem consectetuer libero luctus adipiscing.
Markdown 也允许你偷懒只在整个段落的第一行最前面加上 > ：

> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
id sem consectetuer libero luctus adipiscing.

区块引用可以嵌套（例如：引用内的引用），只要根据层次加上不同数量的 > ：
> This is the first level of quoting.
>
> > This is nested blockquote.
>
> > > > Back to the first level.

引用的区块内也可以使用其他的 Markdown 语法，包括标题、列表、代码区块等。

### 5. 列表
Markdown 支持有序列表和无序列表。 无序列表使用星号、加号或是减号作为列表标记。 示例：

- 列表内容
+ 列表内容
* 列表内容

注意：- + * 跟内容之间都要有一个空格

有序列表则使用数字接着一个英文句点作为标记。 示例：

1. 列表内容
2. 列表内容
3. 列表内容

注意：序号跟内容之间要有空格

很重要的一点是，你在列表标记上使用的数字并不会影响输出的 HTML 结果。

你的标记写成：
1.  Bird
1.  McHale
1.  Parish

甚至：

8. Bird
1. McHale
4. Parish

效果都一样。
你的标记写成： 1. Bird 1. McHale 1. Parish

甚至：

Bird
McHale
Parish
效果都一样，只按第一个数字来排序，因此第一个最好是1。

列表可以嵌套，上一级和下一级之间敲三个空格即可。

* 一级无序列表内容

   * 二级无序列表内容
   * 二级无序列表内容
   * 二级无序列表内容

要让列表看起来更漂亮，你可以把内容用固定的缩进整理好：

*   Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
    Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
    viverra nec, fringilla in, laoreet vitae, risus.
*   Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
    Suspendisse id sem consectetuer libero luctus adipiscing

    有一种偷懒的写法也可以：

*   Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
viverra nec, fringilla in, laoreet vitae, risus.
*   Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
Suspendisse id sem consectetuer libero luctus adipiscing.

列表项目可以包含多个段落，每个项目下的段落都必须缩进 4 个空格或是 1 个制表符：

1.  This is a list item with two paragraphs. Lorem ipsum dolor
    sit amet, consectetuer adipiscing elit. Aliquam hendrerit
    mi posuere lectus.

    Vestibulum enim wisi, viverra nec, fringilla in, laoreet
    vitae, risus. Donec sit amet nisl. Aliquam semper ipsum
    sit amet velit.

2.  Suspendisse id sem consectetuer libero luctus adipiscing.

如果你每行都有缩进，看起来会看好很多，当然，再次地，如果你很懒惰，Markdown 也允许：

*   This is a list item with two paragraphs.

    This is the second paragraph in the list item. You're
only required to indent the first line. Lorem ipsum dolor
sit amet, consectetuer adipiscing elit.

*   Another item in the same list.
  
 此外： 如果要在列表项目内放进引用，那 > 就需要缩进， 如果要放代码区块的话，该区块就需要缩进两次，也就是 8 个空格或是 2 个制表符。

 ### 6. 表格
示例：

| 表头 | 表头  | 表头 |
| ---- | :---: | ---: |
| 内容 | 内容  | 内容 |
| 内容 | 内容  | 内容 |

第二行分割表头和内容。
- 有一个就行，为了对齐，多加了几个
文字默认居左
-两边加：表示文字居中
-右边加：表示文字居右
注：原生的语法两边都要用 | 包起来。此处省略

### 7. 代码
在Markdown中加入代码块有两种方式： 第一种，只要简单地缩进 4 个空格或是 1 个制表符就可以，

这是一个普通段落：

    这是一个代码区块。

(当然，前面要有一个空行和前面的文字分隔开)

第二种方法似乎是更为常用， 单行代码：代码之间分别用一个反引号包起来即可；

这里有一句代码`代码内容`。

代码块：代码之间分别用三个反引号包起来，且两边的反引号单独占一行

``` 
  代码...
  代码...
  代码...
```
还可以在上面的 ``` 后面注明你的代码类型，可以产生相应的代码高亮。

### 8. 段落和换行
一个 Markdown 段落是由一个或多个连续的文本行组成，它的前后要有一个以上的空行（空行的定义是显示上看起来像是空的，便会被视为空行。比方说，若某一行只包含空格和制表符，则该行也会被视为空行）。普通段落不该用空格或制表符来缩进。 我们在两个不同的文字块之间，一定要空行以示区分，不然就会被归入同一文字块中。 Markdown 允许段落内的强迫换行（插入换行符）。 如果想要空一行，在插入处先按入两个以上的空格然后回车，即可。

但有时也可以使用标记来强制空行和空格，比如需要首行缩进的时候： 一个空格大小的表示：\  或 \  两个空格的大小表示：\ 或 \ 不换行空格：\ 或 \ 强制空行： \

## 二、Markdown纯文本进阶语法
上面的语法其实基本的写一些东西已经足够用了，但有时候还想要文档看起来更炫一些，这时候需要一些用于排版的进阶语法，实际上，这里用的就是HTML的标签来实现了。
### 1. 更改字体、大小、颜色
语法：

<font face="黑体">我是黑体字</font>
<font face="微软雅黑">我是微软雅黑</font>
<font face="STCAIYUN">我是华文彩云</font>
<font color=red>我是红色</font>
<font color=#008000>我是绿色</font>
<font color=Blue>我是蓝色</font>
<font size=5>我是尺寸</font>
<font face="黑体" color=green size=5>我是黑体，绿色，尺寸为5</font>

### 2. 为文字添加背景色
由于 style 标签和标签的 style 属性不被支持，所以这里只能是借助 table, tr, td 等表格标签的 bgcolor 属性来实现背景色。故这里对于文字背景色的设置，只是将那一整行看作一个表格，更改了那个格子的背景色（bgcolor）。 语法：

<table><tr><td bgcolor=yellow>背景色yellow</td></tr></table>

### 3. 设置文字居中
<center>居中</center>
<p align="left">左对齐</p>
<p align="right">右对齐</p>

### 4. 加入上下标
使用HTML中下标下标的语法即可, 语法：

H<sub>2</sub>O  CO<sub>2</sub>
爆米<sup>TM</sup>

## 三、Markdown进阶使用
有时候在用Markdown时，我们不止要使用纯文本，还需要插入一些图片，链接等等，由于Markdown只是关注于纯文本，因此这些操作都要通过引用来完成，不像word里面简单的复制粘贴。

### 1. 超链接
Markdown 支持两种形式的链接语法： 行内式和参考式两种形式。

不管是哪一种，链接文字都是用 [方括号] 来标记。

要建立一个行内式的链接，只要在方块括号后面紧接着圆括号并插入网址链接即可，注意方括号和圆括号之间一定不能有空格，如果你还想要加上链接的 title 文字，只要在网址后面，用双引号把 title 文字包起来即可，例如：

This is [an example](http://example.com/ "Title") inline link.

[This link](http://example.net/) has no title attribute.

注：如果想要在新页面中打开的话可以用html语言的a标签代替。

<a href="超链接地址" target="_blank">超链接名</a>

参考式的链接是在链接文字的括号后面再接上另一个方括号，而在第二个方括号里面要填入用以辨识链接的标记：

This is [an example][id] reference-style link.
接着，在文件的任意处，你可以把这个标记的链接内容定义出来:

[id]: http://example.com/  "Optional Title Here"
链接内容的形式为： 方括号（前面可以选择性地加上至多三个空格来缩进），里面输入链接文字 接着一个冒号 接着一个以上的空格或制表符 接着链接的网址 选择性地接着 title 内容，可以用单引号、双引号或是括弧包着 链接网址也可以用尖括号包起来：[id]: <http://example.com/> "Optional Title Here"

链接辨别标签可以有字母、数字、空白和标点符号，但是并不区分大小写。

链接的定义可以放在文件中的任何一个地方，我比较偏好直接放在链接出现段落的后面，你也可以把它放在文件最后面，就像是注解一样。

此外，用这个方法还可以将图片转化为base64编码保存在.md文件中，这将在插入图片中介绍。

下面是一个参考式链接的范例：

I get 10 times more traffic from [Google] [1] than from
[Yahoo] [2] or [MSN] [3].

  [1]: http://google.com/        "Google"
  [2]: http://search.yahoo.com/  "Yahoo Search"
  [3]: http://search.msn.com/    "MSN Search"
还可以直接用链接名称的方式写：

I get 10 times more traffic from [Google][] than from
[Yahoo][] or [MSN][].

  [google]: http://google.com/        "Google"
  [yahoo]:  http://search.yahoo.com/  "Yahoo Search"
  [msn]:    http://search.msn.com/    "MSN Search"
要知道，参考式的链接其实重点不在于它比较好写，而是它比较好读。 使用 Markdown 的参考式链接，可以让文件更像是浏览器最后产生的结果，让你可以把一些标记相关的元数据移到段落文字之外，你就可以增加链接而不让文章的阅读感觉被打断。

### 2. 自动链接
除了上面的超链接方式，Markdown 还支持以比较简短的自动链接形式来处理网址和电子邮件信箱，只要是用尖括号包起来， Markdown 就会自动把它转成链接。 语法：

<http://example.com/>

### 3. 插入图片
很明显地，要在纯文字应用中设计一个「自然」的语法来插入图片是有一定难度的。 Markdown 使用一种和链接很相似的语法来标记图片，同样也允许两种样式： 行内式和参考式。

行内式的图片语法看起来像是：

![Alt pic](/path/to/img.jpg)

![Alt pic](/path/to/img.jpg "Optional title")
详细叙述如下： 一个惊叹号 ! 接着一个方括号，里面放上图片的替代文字 * 接着一个普通括号，里面放上图片的网址或本地路径（可以是相对路径或绝对路径），最后还可以用引号包住并加上 选择性的 '标题' 文字。

参考式的图片语法则长得像这样：

![Alt pic][id]
「id」是图片参考的名称，图片参考的定义方式则和连结参考一样：

[id]: url/to/image  "Optional title attribute"

两个解决方法：
#### 1. 将本地图片上传到github
首先在github中新建一个repo，然后git clone下来，然后把你想要的图片放到这个文件夹中然后上传，然后到GitHub中找到这个图片查看地址，在markdown中引用就好了。

这种方法的优点就在于插入式很灵活，github没有墙，你的文章上传到各个平台，图片也都基本不会丢失或找不到，但缺点就在于图片的管理很不方便，图片一旦多起来，你的本地仓库将会变得很大，而且你的文章可能涉及很多方面，管理也不方便，不过，也算是一个比较理想的解决方案。
#### 2. 把图片存入markdown文件
1. 用base64转码工具把图片转成一段字符串
2. 把字符串填到基础格式中链接的那个位置。
3. 由于图片转成base64编码，会非常的大，一般至少都要上千行，这个时候会发现插入的这一长串字符串会把整个文章分割开，非常影响编写文章时的体验。这时候就可以用参考式，把大段的base64字符串放在文章末尾，然后在文章中通过一个id来调用，文章就不会被分割的这么乱了。
   
这种方法的优点就是图片真的是不会丢啊，相当于直接将图片编码嵌入到文档中，但缺点也是显而易见的，就是base64编码实在是太长了啊，太长了，虽然可以放到文章结尾，但还是太长了，所以目前我还没找到更好的解决方法。

### 4. 调整图片格式
到目前为止， Markdown 还没有办法直接指定图片的宽高，如果需要的话，则可以使用普通的 \


标签。 * 图片位置——居左/居中/居右

利用markdown在编写文档时插入图片是默认靠左，有些时候将图片设置为居中时可以更加的美观，这时就需要在图片的信息前边添加如下语句：

<div align=center>![Alt pic] (http:...)

如果想将图片位于右侧，只需要将center改为right
设置图片大小
<img src="http:..." width = "100" height = "100" div align=right />
如上格式，在图片的最后添加 width = “100” height = “100”，就可以设置图片的大小。也可以在后边输入百分比为多少，如 width = 20% height = 20%， 当然，如果你使用的是base64编码，可以直接将编码放到上面放链接的引号里，也可以设置图片大小，但是放在\


标签里，貌似就不能作为参考式的链接了，所以用base64调整图片大小还是很艰难，也希望大手能指导一下。

### 5. LaTeX 公式 


Markdown还有一大优势就是可以支持 LaTeX 的公式。 \$ 表示行内公式 \$$ 表示整行公式 访问 MathJax 参考更多使用方法。

这里说一个常用的，很多时候，我们在做笔记时候，需要画箭头，然后在箭头上需要写字，这里就可以用LaTeX公式来实现：

$ X\stackrel{F}{\longrightarrow}Y $

### 6. 内容目录
Markdown还有一个很方便的功能，就是可以根据标题自动生成目录。 在段落中填写 [TOC] 以显示全文内容的目录结构

在最后要说的是，Markdown其实还有很多强大的功能，比如画流程图、序列图、甘特图、Mermaid 流程图、Mermaid 序列图， 因为暂时用的比较少，而且上面的语法应该已经足够用了，所以这个就有待我下次再开发把。

Tips： 1. 用于Markdown语法标记的符号和后面的内容之间一定要加上至少一个空格，以便识别。 2. 在Markdown编辑中，你用「Enter」键来敲空行，最多只能空一行，如果想要在显示中有多行空行的话，则要用HTML标签来实现了。