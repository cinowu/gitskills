#gitskills前言
##

# 个人资料汇总 #
1. MyGitHub：https://github.com/cinowu
2. My技术博客：http://my.oschina.net/wisdomperson/blog 
3. My技术博客：http://javacrazyer.iteye.com/
4. My技术博客：http://blog.csdn.net/wjt1989wjt
5. My生活博客：http://wujintao.diandian.com/ 
6. My优酷：http://u.youku.com/Wujintao123
7. My新浪微博：http://weibo.com/u/1747720793 
8. My腾讯微博：http://t.qq.com/huanggaowuqiqiang 
9. My邮箱：jellon.wu@gmail.com
10. My邮箱：cino.wu@gmail.com

#windows安装Git客户端：

Git本来是在linux下开发的，后来又支持了windows版本。

Windows下要使用很多Linux/Unix的工具时，需要Cygwin这样的模拟环境，Git也一样。Cygwin的安装和配置都比较复杂，就不建议你折腾了。不过，有高人已经把模拟环境和Git都打包好了，名叫msysgit，只需要下载一个单独的exe安装程序，其他什么也不用装，绝对好用。msysgit是Windows版的Git，从http://msysgit.github.io/下载，然后按默认选项安装即可。

安装完成后，在开始菜单里找到“Git”->“Git Bash”，蹦出一个类似命令行窗口的东西，就说明Git安装成功！

- Git Bash 乱码解决方法，bash窗口输入： 	git config --global i18n.commitencoding utf-8
- Git Gui  乱码解决方法，bash窗口输入：    git config --global gui.encoding utf-8


#PS
友情附赠国外网友制作的Git Cheat Sheet，建议打印出来备用：[Git Cheat Sheet](http://www.git-tower.com/blog/assets/2013-05-22-git-cheat-sheet/cheat-sheet-large01.png)