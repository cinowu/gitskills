#介绍
##
Aria2 是 Linux CLI 界面下的多线程下载工具，与之前介绍的 axel 类似，但比之更强大。它支持 HTTP/HTTPS, FTP, BitTorrent 和 Metalink 协议，支持多线程下断点续传。

#下载
##
直接安装：sudo apt-get install aria2,或者通过如下方式下载：

1. 下载地址：[http://aria2.sourceforge.net](http://aria2.sourceforge.net)
1. 获取源码：[https://github.com/tatsuhiro-t/aria2](https://github.com/tatsuhiro-t/aria2)
1. 查看文档：[http://aria2.sourceforge.net/manual/en/html/README.html](http://aria2.sourceforge.net/manual/en/html/README.html)
2. gui程序：[http://sourceforge.net/projects/aria2fe/](http://sourceforge.net/projects/aria2fe/)

#使用
##
**解压**
<pre>
/wujintao$ tar zxvf aria2-1.18.3.tar.gz
aria2-1.18.3/
aria2-1.18.3/test-driver
aria2-1.18.3/test/
aria2-1.18.3/test/local-metaurl.meta4
aria2-1.18.3/test/base_uri.xml
aria2-1.18.3/test/metalink4-dosdirtraversal.xml
......
</pre>

**查看**
<pre>
/wujintao/aria2-1.18.3$ ls
ABOUT-NLS       ChangeLog     config.sub    deps        lib              Makefile.in         mingw-release  README         test
aclocal.m4      compile       configure     doc         LICENSE.OpenSSL  makerelease         missing        README.html    test-driver
android-config  config.guess  configure.ac  examples    ltmain.sh        makerelease-osx.mk  NEWS           README.rst
android-make    config.h.in   COPYING       INSTALL     m4               mingw-build-memo    osx-package    script-helper
AUTHORS         config.rpath  depcomp       install-sh  Makefile.am      mingw-config        po             src
</pre>

**编译**
<pre>
/wujintao/aria2-1.18.3$ ./config
config.guess  config.rpath  config.sub    configure
kaifa@hemskf109:~/wujintao/aria2-1.18.3$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
......

/wujintao/aria2-1.18.3$ make
make  all-recursive
make[1]: Entering directory `/home/kaifa/wujintao/aria2-1.18.3'
Making all in po
make[2]: Entering directory `/home/kaifa/wujintao/aria2-1.18.3/po'
make[2]: Leaving directory `/home/kaifa/wujintao/aria2-1.18.3/po'

目前在公司linux make失败
</pre>

**使用**
##
参见：<br/>
[http://wiki.ubuntu.org.cn/Aria2](http://wiki.ubuntu.org.cn/Aria2)<br>
[https://linuxtoy.org/archives/aria2.html](https://linuxtoy.org/archives/aria2.html)

**下载demo连接**
<pre>
http://jaist.dl.sourceforge.net/project/aria2/stable/aria2-1.18.3/aria2-1.18.3-win-32bit-build1.zip
http://jaist.dl.sourceforge.net/project/aria2cremote/stable/0.1.1/Aria2cRemoteControl-0.1.1-win32.exe
http://jaist.dl.sourceforge.net/project/aria2web/Aria2Web_0.1.zip
</pre>