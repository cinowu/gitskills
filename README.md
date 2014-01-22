#gitskills前言
##

#windows安装Git客户端：

Git本来是在linux下开发的，后来又支持了windows版本。

Windows下要使用很多Linux/Unix的工具时，需要Cygwin这样的模拟环境，Git也一样。Cygwin的安装和配置都比较复杂，就不建议你折腾了。不过，有高人已经把模拟环境和Git都打包好了，名叫msysgit，只需要下载一个单独的exe安装程序，其他什么也不用装，绝对好用。msysgit是Windows版的Git，从[http://msysgit.github.io/](http://msysgit.github.io/)下载，然后按默认选项安装即可。

安装完成后，在开始菜单里找到“Git”->“Git Bash”，蹦出一个类似命令行窗口的东西，就说明Git安装成功！

- Git Bash 乱码解决方法，bash窗口输入： 	git config --global i18n.commitencoding utf-8
- Git Gui  乱码解决方法，bash窗口输入：    git config --global gui.encoding utf-8

###另外github官方的客户端也很棒<http://windows.github.com/>

github官方教程：<http://try.github.io/levels/1/challenges/1>


#使用Git(参考雪峰童鞋的)  
##自报家门
>安装完成后，还需要最后一步设置，在命令行输入：
>
>$ git config --global user.name "Your Name"
>
>$ git config --global user.email "email@example.com"
>
>因为Git是分布式版本控制系统，所以，每个机器都必须自报家门：你的名字和Email地址。
>
>注意：git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。

##初始化git仓库
>初始化一个Git仓库，新建一个仓库目录，使用git init命令。
>
>添加文件到Git仓库，分两步：
>
>第一步，使用命令git add ，注意，可反复多次使用，添加多个文件；
>
>第二步，使用命令git commit -m ""，完成。

##查看git实时状态
>
>要随时掌握工作区的状态，使用git status命令。
>
>如果git status告诉你有文件被修改过，用git diff可以查看修改内容。
    
##版本穿越
>
>HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。
>
>穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。
>
>要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。
   
>情况一，修改了工作区的文件，添加了很多内容，还没有git add，想撤销修改，如下：】   
>
> 撤销刚刚工作区的修改，git checkout -- file命令中的“--”很重要，没有“--”，就变成了“创建一个新分支”的命令
>
>git checkout其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。
  
>【情况二，修改了工作区的文件，已经git add,想撤销这次已经发生的git add，如下：】
>
> git reset HEAD file可以把暂存区的修改撤销掉（unstage），重新放回工作区]
  
>【情况三，现在，假设你不但改错了东西，还从暂存区提交到了版本库，怎么办呢？还记得版本回退一节吗？可以回退到上一个版本。
>
>不过，这是有条件的，就是你还没有把自己的本地版本库推送到远程。还记得Git是分布式版本控制系统吗？我们后面会讲到远程版本库，一旦你把“stupid boss”提交推送到远程版本库，你就真的惨了……
】
  
>场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。
 
>场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD file，就回到了场景1，第二步按场景1操作。
 
>场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。

##删除和恢复版本
>命令git rm用于删除一个文件，从版本库中被删除了，这个没法恢复，
>
>另一种情况是删错了，因为版本库里还有呢，所以可以很轻松地把误删的文件恢复到最新版本：git >
>
>checkout -- file。
>如果一个文件已经被提交到版本库，那么你永远不用担心误删，但是要小心，你只能恢复文件到最新版本，
>
>你会丢失最近一次提交后你修改的内容。
 
##本地git仓库关联上github公开仓库 
>本地git仓库关联github上公开的仓库：
>
>在本地git仓库根目录下执行： git remote add origin git@github.com:cinowu/hellogit.git
>
>添加后，远程库的名字就是origin，这是Git默认的叫法，也可以改成别的，但是origin这个名字一看就知道是远程库
 
>第一次推送本地仓库内容到远程github仓库：
>
>git push -u origin master
>
>由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。  
>
>推送成功后，可以立刻在GitHub页面中看到远程库的内容已经和本地一模一样
 从现在起，只要本地作了提交，就可以通过命令： git push origin master
  
  
>
>要关联一个远程库，使用命令git remote add origin git@server-name:path/repo-name.git；
>
>或者git remote add origin https://github.com/cinowu/gitskills.git
>
>关联后，使用命令git push -u origin master第一次推送master分支的所有内容；
   此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改；
  
  
##下载github公开仓库到本地  
>从远程github仓库中拷贝到本地git仓库：
>
>git clone https://github.com/cinowu/gitskills.git
>
>或者git clone git@github.com:cinowu/gitskills.git
  
>使用https除了速度慢以外，还有个最大的麻烦是每次推送都必须输入口令，但是在某些只开放http端口的公司内部就无法使用ssh协议而只能用https。
  
>
>要克隆一个仓库，首先必须知道仓库的地址，然后使用git clone命令克隆。
 Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。
  
>
>【警告】不要使用https:开头的仓库地址，不仅慢，还会导致一系列问题，只需要将 git@github.com:cinowu/gitskills.git
  这个中的用户名cinowu换成github用户名，gitskills换成github仓库名即可。
  

##git分支  
>Git鼓励大量使用分支：
>
>查看分支：git branch
>
>创建分支：git branch name
>
>切换分支：git checkout name
>
>创建+切换分支：git checkout -b name
>
>合并某分支到当前分支：git merge name
>
>合并完之后可以删除分支，但是一般分支不建议删除：git branch -d name
  
##解决冲突
>当Git无法自动合并分支时，就必须首先解决冲突,手动在master上修改。解决冲突后，再提交，合并完成。
>
>用git log --graph命令可以看到分支合并图。
>
>git log --graph --pretty=oneline --abbrev-commit
   

##合并文件   
>git merge --no-ff -m "merge with no-ff" dev
>
>请注意--no-ff参数，表示禁用“Fast forward”：
 合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。
 
  
##分支策略
>在实际开发中，我们应该按照几个基本原则进行分支管理：
  首先，master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；
  那在哪干活呢？干活都在dev分支上，也就是说，dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版本；
  你和你的小伙伴们每个人都在dev分支上干活，每个人都有自己的分支，时不时地往dev分支上合并就可以了。

#BTW
友情附赠国外网友制作的Git Cheat Sheet，建议打印出来备用：[Git Cheat Sheet](http://www.git-tower.com/blog/assets/2013-05-22-git-cheat-sheet/cheat-sheet-large01.png)  


也可以在googlecode上创建git协议的publis repository  
参见我用cino.wu账户在googlecode上创建的git协议的项目<https://code.google.com/p/cino-learn-svn/>  
<https://code.google.com/p/cino-learn-svn/source/checkout>  
创建google code project入口：<https://code.google.com/intl/zh-HK/>


#PS
创建在github上的站点，定制自己的域名：<http://pages.github.com/>  
我的已经建好了<http://cinowu.github.io>

参考怎样创建好看的站点界面和项目:<http://www.worldhello.net/gotgithub/03-project-hosting/050-homepage.html>

作者：[@岁月静好--似水流年](http://weibo.com/u/1747720793)<br/>
2014-01-15 星期三 10:45:21 
