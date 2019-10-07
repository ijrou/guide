#### 远程仓库   GitHub

Git 是分布式版本控制系统，Git仓库可以通过 clone 克隆方式分不到不同机器上，这样每台机器的版本都是一样的了，没有主次之分

安全起见是把一台服务器当做Git服务器来维护，所有人都可以通过Git服务器获取，当Git服务器爆炸了即可通过下面的某台电脑克隆版本库

Github网站提供Git仓库托管服务，本地的Git和GitHub仓库之间传输通过SSH或者HTTPS加密的

第一步：本地创建SSH Key，在用户目录下(Windows 是：C:/User/Administrator   Linux 是 : /root/ )下查看.ssh目录下是否有id-rsa和id-rsa.pub，没有的话创建一个

```
$ ssh-keygen -t rsa -C "youremail@example.com"
```

然后一路回车，使用默认值即可，由于这个Key也不是用于军事目的，所以也无需设置密码

如果一切顺利的话，可以在用户主目录里找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对


第二步：登陆GitHub，打开“Account settings”，“SSH Keys”页面

然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容

**为什么GitHub需要SSH Key呢？**

因为GitHub需要识别出你推送的提交确实是你推送的，而不是别人冒充的，而Git支持SSH协议，所以，GitHub只要知道了你的公钥，就可以确认只有你自己才能推送。

当然，GitHub允许你添加多个Key。假定你有若干电脑，你一会儿在公司提交，一会儿在家里提交，只要把每台电脑的Key都添加到GitHub，就可以在每台电脑上往GitHub推送了。



现在的情景是，你已经在本地创建了一个Git仓库后，又想在GitHub创建一个Git仓库，并且让这两个仓库进行远程同步，这样，GitHub上的仓库既可以作为备份，又可以让其他人通过该仓库来协作，真是一举多得。


首先，登陆GitHub，创建一个新的仓库，如repository name 为：learn_git

根据GitHub的提示，在本地的learngit仓库下运行命令

```
$ git remote add origin git@github.com:你的github名/远程库名
```

添加关联后，远程库的名字就是origin，这是Git默认的叫法，也可以改成别的，但是origin这个名字一看就知道是远程库。

下一步就是把本地库的所有内容推送到远程库上

```
$ git push -u origin master
```

>   当本地版本库与远程github版本库存在差异时，我们需要先将远程github版本库pull获取下来合并，解决冲突后在push到远程仓库上；
>
>   $ git pull origin master --allow-unrelated-histories
>
>   -   --allow-unrelated-histories：该选项可以合并两个独立启动仓库的历史，主要解决本地仓库和远程仓库实际上是独立的两个仓库的问题；
>
>   clone克隆下来的代码无需此操作，也没那么复杂；

把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程

由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。

从现在起，只要本地作了提交，就可以通过命令：

```
$ git push origin master
```

远程代码合并【注：pull=fetch+merge]

```
$git pull --rebase origin master
```



#### 克隆

现在有远程库gitskills ，通过克隆把远程库gitskills克隆到本地上

>   PS：需要 README.MD 文件

克隆到本地：

```
$ git clone git@github.com:你的github名/远程库名
```

Git支持多种协议，默认的git://使用ssh，但也可以使用https等其他协议。

使用https除了速度慢以外，还有个最大的麻烦是每次推送都必须输入口令，但是在某些只开放http端口的公司内部就无法使用ssh协议而只能用https。
