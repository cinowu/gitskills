#介绍
##
Axel是一个命令行下载工具，支持多来源、多线程,通过打开多个 HTTP/FTP 连接来将一个文件进行分段下载，从而达到加速下载的目的。对于下载大文件，该工具将特别有用。

#安装与下载
##
- **linux机器** <br/>
  方式一【安装命令】：sudo apt-get install axel <br/>
  方式二【安装命令】：apt://axel<br/>
  方式三【下载安装文件】：http://pkgs.repoforge.org/axel/<br/>
  方式四【下载压缩文件】：https://github.com/emiraga/axel 【推荐这种】

#使用方式（以第四种为例）
##
**解压**
<pre>
/wujintao$ unzip -d axel axel-master.zip
Archive:  axel-master.zip
0b64cc20c4bb09c26ee3bac24baccbbe4e1a81df
   creating: axel/axel-master/
 extracting: axel/axel-master/.gitignore
  inflating: axel/axel-master/API
  inflating: axel/axel-master/CHANGES
  inflating: axel/axel-master/COPYING
  inflating: axel/axel-master/CREDITS
  inflating: axel/axel-master/Makefile
  inflating: axel/axel-master/README
  inflating: axel/axel-master/README.md
  inflating: axel/axel-master/axel.1
  inflating: axel/axel-master/axel.c
  inflating: axel/axel-master/axel.h
  inflating: axel/axel-master/axel_zh_CN.1
  inflating: axel/axel-master/axelrc.example
  inflating: axel/axel-master/conf.c
  inflating: axel/axel-master/conf.h
  inflating: axel/axel-master/configure
  inflating: axel/axel-master/conn.c
  inflating: axel/axel-master/conn.h
  inflating: axel/axel-master/de.po
  inflating: axel/axel-master/ftp.c
  inflating: axel/axel-master/ftp.h
   creating: axel/axel-master/gui/
   creating: axel/axel-master/gui/kapt/
  inflating: axel/axel-master/gui/kapt/Makefile
  inflating: axel/axel-master/gui/kapt/axel-kapt
  inflating: axel/axel-master/gui/kapt/axel-kapt.1
  inflating: axel/axel-master/gui/kapt/axel-kapt.desktop
  inflating: axel/axel-master/http.c
  inflating: axel/axel-master/http.h
  inflating: axel/axel-master/nl.po
  inflating: axel/axel-master/ru.po
  inflating: axel/axel-master/search.c
  inflating: axel/axel-master/search.h
  inflating: axel/axel-master/tcp.c
  inflating: axel/axel-master/tcp.h
  inflating: axel/axel-master/text.c
  inflating: axel/axel-master/zh_CN.po

/wujintao$ cd axel/axel-master/
/wujintao/axel/axel-master$ ls
API     axel.h          CHANGES  configure  COPYING  ftp.c  http.c    nl.po      ru.po     tcp.c   zh_CN.po
axel.1  axelrc.example  conf.c   conn.c     CREDITS  ftp.h  http.h    README     search.c  tcp.h
axel.c  axel_zh_CN.1    conf.h   conn.h     de.po    gui    Makefile  README.md  search.h  text.c
</pre>

**执行编译**
<pre>
/wujintao/axel/axel-master$ ./configure
The strip option is enabled. This should not be a problem usually, but on some
systems it breaks stuff.

Configuration done:
  Internationalization enabled.
  Debugging disabled.
  Binary stripping enabled.

/wujintao/axel/axel-master$ make
gcc -c axel.c -o axel.o -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -Os
gcc -c conf.c -o conf.o -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -Os
gcc -c conn.c -o conn.o -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -Os
gcc -c ftp.c -o ftp.o -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -Os
gcc -c http.c -o http.o -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -Os
gcc -c search.c -o search.o -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -Os
gcc -c tcp.c -o tcp.o -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -Os
tcp.c: 在函数‘get_if_ip’中:
tcp.c:98: 警告：dereferencing pointer ‘x’ does break strict-aliasing rules
tcp.c:97: 附注：initialized from here
gcc -c text.c -o text.o -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -Os
gcc *.o -o axel  -lpthread
strip axel
msgfmt -vo nl.mo nl.po
40 条已翻译消息，6 条模糊消息，4 条未翻译消息.
msgfmt -vo de.mo de.po
46 条已翻译消息，4 条模糊消息.
msgfmt -vo ru.mo ru.po
46 条已翻译消息，2 条模糊消息，2 条未翻译消息.
msgfmt -vo zh_CN.mo zh_CN.po
42 条已翻译消息，6 条模糊消息，2 条未翻译消息.
</pre>

**此时查看，编译出来了一个axel执行文件**
<pre>
/wujintao/axel/axel-master$ ll
总用量 400K
drwxrwxr-x 3 kaifa kaifa 4.0K  1月  8 11:24 ./
drwxrwxr-x 3 kaifa kaifa 4.0K  1月  8 11:07 ../
-rw-rw-r-- 1 kaifa kaifa 9.1K  1月 13 2011 API
-rwxrwxr-x 1 kaifa kaifa  36K  1月  8 11:24 axel*
......
</pre>

**使用**
<pre>
1. 一般使用：
axel url（下载文件地址）

2. 限制连接数：
加上 -n 参数，如 -n 5，即打开 5 个连接，也就是5个线程同时
axel -n 20 url
</pre>


哈哈，可以明显看到速度上升，妈妈再也不用担心wget下载慢啦