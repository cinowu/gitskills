##MarkDown资源
1. Markdown项目主页：<http://daringfireball.net/projects/markdown/>
1. Markdown语法说明（中文版）：<http://wowubuntu.com/markdown/>


##Markdown工具
1. Windows：MarkdownPad, MEditor
1. Linux：ReText
1. Mac：Mou
1. Chrome插件：Made, Markdown Here
1. Sublime Text 2: 跨平台编辑器，可通过插件支持Markdown
1. Pandoc: 强大的文本编译工具，支持各种文档格式互转


##提示:本人整理MarkDown语法O(∩_∩)O~，往下看##

###1.分割线：
<pre>
##
* * *
***
*****
---
---------------------------------------
</pre>

###2.原始文件
>保持原段落文字不变，可以选用`<pre>我是文字等</pre>`元素

>要添加代码或者原始文本XML等，只需要添加进来整体选中按下tab键即可，  
或者每一行代码前都空出四个空格也行

>保持html等原始标签：使用反引号``,反引号在键盘数字1键的旁边

> I strongly recommend against using any ` <blink> ` tags.

> I wish SmartyPants used named entities like `&mdash;`

> instead of decimal-encoded entites like `&#8212;`.

> 或者使用特殊html标签的原型比如<对应`&lt;`,&对应`&amp;`等

###3.换行
<pre>
每一行最后加上两个空格，接下来输出的就是换行
</pre>

###4.标题、引用
<pre>
#表示这是一级标题
##表示这是二级标题(注意二级标题下会带一条横线)
###表示这是三级标题
……
###### 最小是六级标题

也可以这样表示大标题(注意写完这行下一行加上=表示大标题)
=

这样表示小标题(注意写完这行下一行加上-表示小标题)
-
>aaaaa 表示引用

> This is a blockquote.
> 
> This is the second paragraph in the blockquote.
>
> ## This is an H2 in a blockquote
</pre>

###5.分段
<pre>
单个回车,视为空格。
连续回车,才能分段。
</pre>

###6.斜体、粗体
<pre>
*这些文字显示为斜体*
**这些文字显示为粗体**
</pre>

###7.列表、嵌套列表
<pre>
A.无序列表如下：

- 这是无序列表项目
- 这是无序列表项目
- 这是无序列表项目

[注]两个列表之间不能相邻，否则会解释为嵌套的列表

B.有序列表如下：

1. 这是有序列表项目
2. 这是有序列表项目
3. 这是有序列表项目

C.嵌套列表如下：

- 外层列表项目
 + 内层列表项目
 + 内层无序列表项目
 + 内层列表项目
- 外层列表项目
</pre>

###8.超链接、图片链接
>自动链接格式：`<http://example.com/>`  就是在链接两边加上<和>  
>自动链接：`<sample@126.com>`  `<http://www.baidu.com>`  

<pre>
文字链接格式：This is an [example link](http://example.com/).
文字链接：[图灵社区](http://www.ituring.com.cn)
加上标题alt的文字链接：[example link](http://example.com/ "With a Title").

图片链接格式：![alt text](/path/to/img.jpg "Title")
图片链接： ![这是一个Logo图像](http://www.turingbook.com/Content/img/Turing.Gif)

索引链接：
[图灵社区][1]
![图灵社区Logo][2]
[1]:http://www.ituring.com.cn
[2]:http://www.ituring.com.cn/Content/img/Turing.Gif

或者：
I get 10 times more traffic from [Google][1] than from
[Yahoo][2] or [MSN][3].
[1]: http://google.com/ "Google"
[2]: http://search.yahoo.com/ "Yahoo Search"
[3]: http://search.msn.com/ "MSN Search"

或者：
I start my morning with a cup of coffee and
[The New York Times][NY Times].
[ny times]: http://www.nytimes.com/
</pre>

###9.转义普通字符
<pre>
markdown支持在字符前加上\对字符保持原型进行转义
\*literal asterisks\*

目前\支持在加在如下字符前可起到转义作用：
\   反斜线
`   反引号
*   星号
_   底线
{}  花括号
[]  方括号
()  括弧
#   井字号
+   加号
-   减号
.   英文句点
!   惊叹号
</pre>

###10.关于表格
A.关于表格的处理，网上有人说了这么一种方式：  


1. 从word或excel中复制表格
1. 打开[此链接](http://pressbin.com/tools/excel_to_html_table/index.html)
1. 贴上复制的文字，然后按convert，就会得到这个表格的代码


以上这种做法生成的HTML代码粘贴到MarkDownPad的确能预览，方法可行，就是麻烦

B.我更倾向于另一种方式：  
这种方式得到的结果虽然不是HTML代码，也不能在MarkDownPad预览，
但是提交到github上就是标准表格，这就是万能的[Tables Generator](http://www.tablesgenerator.com/)

  
Tables Generator 支持四种格式：LaTeX、HTML、Markdown、TEXT，先在 Table > Set size 中设置表格大小，然后填充数据，设置格式，就能在页面下面找到生成的结果，将结果复制到md文件中即可  

因为本文讲的是MarkDown，所以用<http://www.tablesgenerator.com/markdown_tables>这个啦




作者：[@岁月静好--似水流年](http://weibo.com/u/1747720793)<br/>
2014-01-15 星期三 10:45:16 