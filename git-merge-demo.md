#前言
---
以下两个实例用以分析在不同时间点，版本不同步的情况下针对同一文件修改的情形。
这种情形push出现问题，我提供了如下两种解决的方案,仅供参考。




#解决冲突实例1：（不能自动合并成功的）
- 时间顺序为时间1、时间2、时间3，从先到后。
- 以readme.txt这个文件的改动为例。


##时间1
github上branch master的这个文件和本地git branch的这个文件版本保持一致，内容如下：  
<pre>
refer to see the help
</pre>



##时间2
在github上branch master的这个文件修改如下，然后提交上传：
<pre>
refer to see the
wujintao
</pre>



##时间3
本地（没更新时间2的提交修改版本的情况下）修改这个文件如下：
<pre>
refer to see the img
周杰伦
赵薇
</pre>

提交本地

- git add readme.txt
- git commit readme.txt -m "modify something"
- git push origin 这一步提交报错：
<pre>
To git@github.com:cinowu/gitskills.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'git@github.com:cinowu/gitskills.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
</pre>

##解决方案：
###1)git pull将线上最新的自动merge到本地：
针对这个例子， 报错如下：
<pre>
$ git pull
Enter passphrase for key '/c/Users/Administrator/.ssh/id_rsa':
remote: Counting objects: 5, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 0 (delta 0)
Unpacking objects: 100% (3/3), done.
From github.com:cinowu/gitskills
   d4cf4df..13eeb4e  master     -> origin/master
Auto-merging readme.txt
CONFLICT (content): Merge conflict in readme.txt
Automatic merge failed; fix conflicts and then commit the result.
</pre>
意思是要我们手动修复冲突，然后提交结果

###2)这个时候github上和本地的readme.txt冲突信息已经在内容中了，打开readme.txt
<pre>
<<<<<<< HEAD
refer to see the img
周杰伦
赵薇
=======
refer to see the
wujintao
>>>>>>> 13eeb4ed12e7ecb7db26dc32b5e5fd9a4cf79d4c
</pre>


###3）分析下这个文件
======分割线上是本地改动后的，======分割线下是线上改动后的，这样对比后，我们该删除的就删除，然后保存重新提交。我们最终改动后如下：
<pre>
refer to see the
周杰伦
赵薇
</pre>

<font color='red'>
由于这一步有手动修改参与进来，所以必须重新走一次提交流程，git add somefile，然后git commit -m "",最后用git gui上传(也就是git push origin命令)即可解决问题
</font>






#解决冲突实例2：（可以自动合并冲突成功的）
- 时间顺序为时间1、时间2、时间3，从先到后。
- 以readme.txt这个文件的改动为例。

##时间1
github上branch master的这个文件和本地git branch的这个文件版本保持一致，内容如下：
<pre>
refer to see the
周杰伦
赵薇
</pre>

##时间2
在github上branch master的这个文件修改如下，然后提交上传：
<pre>
refer to see the
周杰伦
赵薇
刘德华，赵本山
冯小刚，张艺谋
</pre>

##时间3
本地（没更新时间2的提交修改版本的情况下）修改这个文件如下：
<pre>
refer to see the
周杰伦
我是王力宏，我是潘玮柏
赵薇
</pre>


提交本地  

- git add readme.txt
- git commit readme.txt -m "modify something"
- git push origin 这一步提交报错：
<pre>
Enter passphrase for key '/c/Users/Administrator/.ssh/id_rsa':
To git@github.com:cinowu/gitskills.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'git@github.com:cinowu/gitskills.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
</pre>


##解决方案：
###1)git pull将线上最新的自动merge到本地：
<pre>
$ git pull
Enter passphrase for key '/c/Users/Administrator/.ssh/id_rsa':
remote: Counting objects: 5, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 1), reused 0 (delta 0)
Unpacking objects: 100% (3/3), done.
From github.com:cinowu/gitskills
   bd1fda9..d7fb2a6  master     -> origin/master
Auto-merging readme.txt
Merge made by the 'recursive' strategy.
 readme.txt | 2 ++
 1 file changed, 2 insertions(+)
</pre>

###2）这个跟解决冲突方案1的git pull不一样
自动merge成功了，我们来看下最终自动merge后的结果：
<pre>
refer to see the
周杰伦
我是王力宏，我是潘玮柏
赵薇
刘德华，赵本山
冯小刚，张艺谋
</pre>

<font color='red'>嗯，没错，就应该是这样的结果，由于是系统自动合并了提交的版本，不涉及人工修改本地，所以直接git gui直接上传(也就是git push origin命令)即可解决问题</font>



#总结
1）能够通过git pull自动合并成功的，说明，我们在github上改动的和在本地改动的都是新增了几行，或者删除了几行，而没有都在同一行进行改动，所以能自动合并成功。  
2）反之，如果你在github上和在本地都改过了同一行，那么git pull之后就得手动解决冲突了


#BTW
---
为了避免这种问题，要养成一种习惯  
1）跟使用SVN一样，每天来到公司第一件事情就是:  
synchronize with repository,选择性的svn update，或者合并到本地。

2）在git本地修改的时候，尽量做到，改之前更新下远程仓库代码，改完后再次更新下远程仓库代码。
git也有类似svn update操作，参考以下示例：
##时间1
本地和github上readme.txt版本一致，内容一样，如下：
<pre>
refer to see the
周杰伦
我是王力宏，我是潘玮柏
赵薇
刘德华，赵本山
冯小刚，张艺谋
</pre>
##时间2
githu修改然后上传，如下：
<pre>
refer to see the
周杰伦
我是王力宏，我是潘玮柏
赵薇
刘德华，赵本山
冯小刚，张艺谋
马上有钱
</pre>

<font color='red'>更新github远程所有</font>（此时如果有其他文件也有更新也会更新到本地）最新变化到本地：  
>git pull
<pre>
$ git pull
Enter passphrase for key '/c/Users/Administrator/.ssh/id_rsa':
Updating b93312f..ebeb834
Fast-forward
 readme.txt | 1 +
 1 file changed, 1 insertion(+)
</pre>

这个时候看本地readme.txt果然是跟github一样的啦  

[注意]  
git pull仅仅针对，<font color='red'>本地没有发生变化后，github服务器上发生变化</font>，然后会将github上相同文件down下来。  

如果github上发生变化，本地也发生变化，那么git pull将对这样的文件不起作用。除非你先git add somefile然后git commit -m "" 之后，才能git pull进行github和本地相同文件的合并，
能系统自动合并成功的，就直接git push origin,不能合并成功的，手动解决冲突，然后重新执行git add somefile,git commit -m "",git push origin这些操作。



有没有单独<font color='red'>更新某个文件[直接覆盖本地修改]</font>的命令呢？有的，命令格式如下：  
>git checkout [some-older-commit-ref] a-file.txt


some-older-commit-ref就是你github上最新提交的版本号,比如我当前提交最新的版本号<https://github.com/cinowu/gitskills/commit/011adb04f334e47374fde043e2a47d36b290e513>
这个中的011adb04f334e47374fde043e2a47d36b290e513即是。

执行如下命令，即可获得远程github单文件更新
>git checkout 011adb04f334e47374fde043e2a47d36b290e513 readme.txt


有没有单独文件更新+合并操作的命令呢，事实上是没有的。

##注意

1. 如果想拿远端git服务器上的最新版本(或某个特定版本)覆盖本地的修改,可以使用git pull命令,
但这会全面更新本地代码库和工作拷贝.  

2. 如果更新单独的某个文件，这需要指定远程git服务器上这个文件最后一次提交的版本号，注意这会覆盖本地这个文件的修改。  
git checkout [some-older-commit-ref] a-file.txt

3. 如果想放弃本地工作拷贝所做修改,可以使用git checkout file/to/path命令,
但该命令只能用本地库覆盖你的工作拷贝,<font color='red'>并不能取得远端版本的更新</font>.


这条命令把当前目录所有修改的文件 从HEAD中签出并且把它恢复成未修改时的样子.
注意：在使用git checkout时，如果其对应的文件被修改过，那么该修改会被覆盖掉。

