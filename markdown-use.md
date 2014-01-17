##Markdown是什么
Markdown 是一种轻量级标记语言，创始人为John Gruber和Aaron Swartz。它允许人们“使用易读易写的纯文本格式编写文档，然后转换成有效的XHTML(或者HTML)文档”。这种语言吸收了很多在电子邮件中已有的纯文本标记的特性。 [1]
简单一句话就是：用纯文本写作，同时用直观的轻量级标记来格式化文档。

##为什么要使用纯文本创作
我的哲学是，任何基于字符的创作都应该是内容至上（除了书法）。这包括写小说，写
论文，或者是写代码。在创作过程中，尤其是前期创作中，任何格式都是一种多余。这
一点大家可以想像一下作家用纸笔写小说，纸上总不能高亮或者加粗吧？用内容说话才
是王道。


##为什么要用Markdown
windows下常用的编辑工具是word,mac上常用的编辑工具是page,linux上常用的编辑工具就是vim了，一份文章编辑完后为了要在不同平台中保存完整的模样时就必需同时准备多种文本格式的文件，这是多么痛苦的一件事。我们写作的初衷是为了写作呀，反而被这些格式烦恼。所以我们要用Markdown,它让你关注内容，格式怎么显示不是要你在写得时候关注的。而在写Markdown时你只需要用一个纯文本的方式进行，不用担心平台与格式的困扰。


##MarkDown资源
1. Markdown项目主页：<http://daringfireball.net/projects/markdown/>
1. Markdown语法说明（中文版）：<http://wowubuntu.com/markdown/>


##Markdown工具
1. Windows：[MarkdownPad](http://markdownpad.com/), MEditor
1. Linux：ReText
1. Mac：[Mou](http://mouapp.com/)
1. Chrome插件：Made, Markdown Here
1. Sublime Text 2: 跨平台编辑器，可通过插件支持Markdown
1. Pandoc: 强大的文本编译工具，支持各种文档格式互转


---

##什么是Pandoc
Markdown本身是为了方便输出到HTML格式的。可是后来大家不局限于只是生成HTML
网页，而Pandoc就是为了解决这种需要。通过Pandoc，原始的Markdown文本可以顺利
的转换成Word文档（.docx），OpenOffice文档（.odt），或者是TeX文档（.tex）等等等等。
MarkDownPad编辑器虽然可以转换为HTML文件，但是转换PDF等就需要升级专业版收费了.  
当然，Pandoc Markdown不是万能的，表格、复杂公式、多国语言、上下标、交叉引用、图表对齐较多的场合，它并不适合。但是需要互动、实时展现、更快输出的场合，Pandoc Markdown等值得大力推荐。未来互联网会逼使写作趋简。需要更快发表、互动输出与交流的场合，也会越来越多。比如课堂作业、企业内部交流、个人博客。用它节省的时间是写作时比较关键的"创作时间"而非"排版时间"。

##为什么Markdown+Pandoc的组合让我动心
1. 轻量、简单易学、上手容易。
2. 能够顺利转换成Word文档。毕竟周围的人用Word还是不少，能够顺利和他们分享文档
也是我的基本需求之一。这点Pandoc可以解决。
3. 能够转成TeX文档。这个对我来说也是必须的，目前为止Markdown对数学和表格的支持
还是有些弱。Pandoc可以将支持表格和公式。

##安装Pandoc
1. 下载依赖环境[hackshell](http://www.haskell.org/platform/)安装程序
1. 下载[pandoc](https://code.google.com/p/pandoc/downloads/list)安装程序  
2. 如果需要输出pdf格式，还得下载[LaTeX](http://miktex.org/download)安装程序

或者参考[这里](http://johnmacfarlane.net/pandoc/installing.html)怎样安装Pandoc

##使用Pandoc
###查看版本
>pandoc --version

###查看命令帮助
>pandoc --help  

可以看到pandoc主要支持的输入与输出格式：
<pre>
Input formats:  native, json, markdown, markdown+lhs, rst, rst+lhs, docbook,
                textile, html, latex, latex+lhs

Output formats: native, json, html, html5, html+lhs, html5+lhs, s5, slidy,
                slideous, dzslides, docbook, opendocument, latex, latex+lhs,
                beamer, beamer+lhs, context, texinfo, man, markdown,
                markdown+lhs, plain, rst, rst+lhs, mediawiki, textile, rtf, org,
                asciidoc, odt, docx, epub
</pre>
看见没，markdown只是pandoc输入格式的一种，它支持更多其他输入格式文件。
上述语言的互转关系，可以看看作者制作的这份[壮观的图](http://johnmacfarlane.net/pandoc/diagram.png)，从中可以看出Pandoc的强大。这年头，哲学系教授会写程序，还是Haskell，伤不起啊


###转换文件
####常用参数
- -f 输入格式（如果没有制定格式，则根据后缀名判断，如果没后缀名，则默认为markdown）
- -t 输输出格式（默认为html）
- -o 如果没有的话（默认是STDOUT）

####Pandoc格式转换命令
最简单转换为html命令:pandoc xxx.txt -o yyy.html  
a: txt转换为html格式。这里--ascii可以避免转成utf-8编码，这样中文在浏览器上就不会乱码了。命令为  
>pandoc -f markdown -t html higrid.net.txt -o newfile.html
>
>pandoc --ascii higrid.net.txt -o newfile.html


b: txt转为pdf格式。注意，为了正确转换中文文本，请修改模板文件，在模板文件第一行下方加入 \usepackage{ctex} 命令为  
>pandoc --latex-engine=xelatex yourfile.txt -o newfile.pdf

c: txt转换为doc格式。  
>pandoc yourfile.txt -o newfile.doc


md转换为与上面类似，只需将youfile.txt换成youfile.md。  
>



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

###10.关于代码块和着色


1）Markdown 会用`<pre>` 和 `<code>`标签来把代码区块包起来，这种情况代码不会着色，在MarkDownDad可以预览出效果。  
用法`<pre><code>代码</code></pre>`.

2）使用格式如下  
<pre>
```java

代码贴在中间 
 
 ```
</pre>
注意上面的"`"符号是键盘数字1左边那个键敲出来的，并且是什么语言就写什么,我是java开所以在那开头的三个符号之后就跟上了java,当然可以将java换成c,python,ruby,go等，markdown会自动着色，但是在MarkDownDad编辑器中看不出来预览效果  
实例如下：


```java
public String callSGCCService(String operationName,String inputXML,String serviceName,String serverContextRoot)
    {
        StringBuilder result=null;
        try
        {
            String endpoint = serverContextRoot+"/services/"+serviceName;
            Service service = new Service();// 创建一个服务(service)调用(call)
            Call call = (Call)service.createCall();// 通过service创建call对象
            call.setTargetEndpointAddress(new java.net.URL(endpoint));// 设置service所在URL
            call.setOperationName(new QName("http://service.yupont.com",operationName));
            call.setUseSOAPAction(true);
            String result1 = (String)call.invoke(new Object[] {inputXML});
            System.out.println(result1);
            result=new StringBuilder(result1);
            result.append("@@@@@");
            result.append(XMLUtil.getNodeTxtByNodeName(XMLUtil.strToXML(result1).getRootElement(), "URL"));
        }
        catch (Exception e)
        {
            System.err.println(e.toString());
        }
        return result.toString();
    }
```


###11.关于表格
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