# Git 与 GitHub

## Git 的起源

#### "自由主义( 开源 ) 教皇" 林纳斯·托瓦兹

* Linux
* Git



#### Git 是什么？

* Git 是目前世界上最先进的<font color='red'>分布式</font>版本控制工具( 没有之一 )



## Git 的使用

#### Git 的安装

* Windows git 下载地址 :

  1. [Git - Downloading Package (git-scm.com)](https://git-scm.com/download/win)
  2. 下载 -> 默认选项安装
  3. 桌面右键 点击 `Git Bash Here`  即可看到一个终端窗口
  4. 在终端内输入 git --version 如果看到版本信息即安装成功 

* 安装完成后，需要最后一步设置，在终端内输入(<font color='red'>**不要复制 英文输入法下手打**</font>)

  1. <font color ='blue'>**git config --global user.name**</font>"<font color = 'red'>**Your Name**</font>"

  2. <font color= 'blue'>**git config --global user.email**</font>"<font color = 'red'>**email@xxx.com**</font>"

     **备注：**以上二步的姓名和邮箱可以随意更改，建议使用自己的

  3. <font color='blue'>**git config user.name**</font> 用于查看配置的姓名

  4. <font color='blue'>**git config user.email**</font> 用于查看配置的邮箱

  5. 因为 Git 是分布式版本控制系统，所以每个机器必须配置：用户名和email地址



#### 常用 Linux命令( 部分 )

* mkdir xxx 新建文件夹
* vi x.txt 新建/编辑一个名为 x 的 txt 文件
  * 输入 i 进入编辑模式
  * Esc + : +wq    保存并退出
  * Esc + : + q!     不保存退出
* cd xxx 进入一个名为 xxx 的文件夹
* cd .. 返回上一级目录
* ls 列出当前文件夹所有的文件
* pwd 显示当前目录
* cat x.txt 显示 名为 x 的 txt 文件的内容
* clear 清屏( 需要注意 : cmd 控制台中 cls 为清屏  )



#### 工作区+版本区+暂存区

* 工作区 ( working Directory ) : 简单的理解 —— 你在电脑中能看到的目录
* 暂存区 ( stage ) : 介于 工作区 和 版本区 中间，是工作区到版本区的必经之路
* 版本库 ( Repository ) : 工作区有一个隐藏目录 .git ,这个文件夹不算工作区，而是 Git 的版本库
  * 第一步 : git add   把文件添加进暂存区
  * 第二步 : git commit  把暂存区的所有内容提交到当前版本库  



#### 创建版本库

* <font color='pink' >**git init** </font>命令 : 初始化版本库
  * 创建成功会提示 : <font color='yellowgreen'>**Initialized empty Git repository in C:/Users/31195/Desktop/xxx/.git/**</font>
  * 目录上会多一个 .git 的文件夹( 没有显示的请打开 显示隐藏文件 )，这个文件夹是 Git 来跟踪管理版本库的，不要去修改/删除里面的内容
* <font color = 'pink'>**git add x.xx**</font> 命令 : 添加指定文件到暂存区
  * 没有任何提示，代表提交成功( Linux的设计理念 )
  * 若未初始化，则会提示: <font color='red'>**fatal: not a git repository (or any of the parent directories): .git**</font>
  * 失败则会提示 : <font color='red'>**fatal: pathspec 'x.xx' did not match any files**</font>
  * 可能出现：<font color='red'>**warning: LF will be replaced by CRLF in xxxx**</font>
    * 原因 : Linux和Windows的换行符不一致导致
    * 解决方法 :执行 <font color='blue'>**git config --global core.autocrlf false**</font>
* 怎么查看文件有没有添加成功
  * <font color='blue'>**git status**</font>
    * 显示<font color='red'> 红色 </font>则未提交到暂存区
    * 显示<font color='green'> 绿色 </font>则已经提交到暂存区

* <font color='pink'>**git commit -m '对本次提交的描述'**</font>

  * 显示则代表 已经成功提交到版本库中

    ```bas
    [master (root-commit) 1c2f825] xxxx
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 "\346\226\260\345\273\272\346\226\207\346\234\254\346\226\207\346\241\243.txt"
    
    ```

  * 如果只输入<font color='red'>**git commit**</font>会出问题，这时需要 ESC + : + q! 退出即可

<img src="https://coco-img.oss-cn-hangzhou.aliyuncs.com/img/git%E4%B8%89%E5%8C%BA%E5%9B%BE%E7%A4%BA.png" alt="git三区图示" style="zoom:80%;" />



#### 差异对比

* <font color='pink'>**git diff**</font> : 比较暂存区和工作区

<img src="https://coco-img.oss-cn-hangzhou.aliyuncs.com/img/05_1.png" alt="05_1" style="zoom: 80%;" />

* <font color='pink'>**git diff --cached**</font> : 比较版本库与暂存区 

* <font color='pink'>**git diff master**</font> : 比较版本库和工作区

  <img src="https://coco-img.oss-cn-hangzhou.aliyuncs.com/img/05_3.png" alt="05_3" style="zoom:80%;" />
  
  

#### 日志 + 版本号

* <font color='pink'>**git log**</font> : 显示从最近到最远的所有提交日志

  <img src="https://coco-img.oss-cn-hangzhou.aliyuncs.com/img/06_1.png" alt="06_1" style="zoom: 80%;" />

* <font color='pink'>**git reflog**</font> : 显示每次提交 ( commit ) 的 commit id

  <img src="https://coco-img.oss-cn-hangzhou.aliyuncs.com/img/06_2-1629362141043.png" alt="06_2" style="zoom:80%;" />

#### 版本回退 + 版本穿梭 + 版本撤销

* <font color='pink'>**git reset --hard HEAD^**</font> 	版本回退( 回退一次提交 )

* <font color='pink'>**git reset --hard 版本号**</font>	回退到指定<font color='red'>版本号</font>的 commit id 版本

* <font color='pink'>**git reset HEAD**</font> 	用`版本库`中的文件去替换`暂存区`的全部文件

* <font color='pink'>**git checkout --x.xxx**</font>	用`暂存区的指定文件`去替换`工作区的指定文件`		<font color ='red'>**危险**</font>

* <font color='pink'>**git checkout HEAD x.xxx**</font>	用`版本库中的文件`替换`暂存区`和`工作区`的文件		<font color ='red'>**危险**</font>

* <font color='pink'>**git rm --cached x.xxx**</font>	从`暂存区`删除文件

  

#### 删除文件

* <font color ='pink'>**git rm x.xxx**</font> 删除文件
* <font color ='pink'>**git rm -r xxxx**</font> 删除文件夹
* **常见问题**

<img src="https://coco-img.oss-cn-hangzhou.aliyuncs.com/img/08_1.png" alt="08_1" style="zoom:80%;" />

#### Git 完整图示

![08_2](https://coco-img.oss-cn-hangzhou.aliyuncs.com/img/08_2.png)

#### 分支

* <font color='pink'>**git checkout -b dev**</font> 		创建 dev 分支，并切换到 dev 分支
* <font color='pink'>**git branch**</font> 		查看当前分支
* <font color='pink'>**git checkout master**</font>		切换到主分支
* <font color='pink'>**git merge dev**</font>		合并 dev 分支到当前分支
* <font color='pink'>**git branch -d dev**</font>		删除指定分支
* <font color='pink'>**git diff 分支1 分支2**</font>		显示出两个分支之间所有差异文件的详细差异
* <font color='pink'>**git diff 分支1 分支2 --stat**</font>		显示出两个分支之间所有差异文件列表
* <font color='pink'>**git diff 分支1 分支2 x.xxx**</font>		显示指定文件的详细差异

<img src="https://coco-img.oss-cn-hangzhou.aliyuncs.com/img/9_1.png" alt="9_1" style="zoom:90%;" />

#### 版本冲突

* 合并分支时，如果在<font color ='red'>同一个文件的同一个地方，都修改了或新增内容</font>会引起版本冲突
* 解决版本冲突最好的办法是借助 Webstorm ( 或 VS Code ) 解决，简单且高效

<img src="https://coco-img.oss-cn-hangzhou.aliyuncs.com/img/10_1.png" alt="10_1" style="zoom:80%;" />



## GitHub

#### GitHub 是什么？

* GitHub 是一个 Git 项目托管网站

  

#### GitHub 能做什么？

* 能够分享你的代码或其他开发人员配合一起开发

* GitHub 是一个基于 Git 的代码托管平台，Git 并不像 SVN 那样有一个中心服务器。目前我们使用到的 Git 命令都是在本地执行，需要将数据放到一台其他开发人员能够连接的服务器上

  

#### GitHub 远程仓库的使用

###### 关联 : 本地有仓库，要和远程仓库做关联

* <font color ='pink'>**git init**</font>	

* <font color ='pink'>**git add ***</font>

* <font color ='pink'>**git commit -m 'this is NO.1 commit'**</font>

* <font color ='pink'>**在 GitHub 上创建一个远程仓库**</font>

* <font color ='purple'>**git remote add origin https://<token令牌>@github.com/<GitHub用户名>/<仓库名>**</font> 		<font color ='red'>**2021年8月14号更新后，传统的提交方式已经失效。需要采用token令牌的方式提交**</font>

  * **token令牌获取方式**

    1. 在右侧点击头像 点击 Settings<img src="https://coco-img.oss-cn-hangzhou.aliyuncs.com/img/image-20210819172238726.png" alt="image-20210819172238726" style="zoom:80%;" />
    2. 点击图上红色框<img src="https://coco-img.oss-cn-hangzhou.aliyuncs.com/img/image-20210819172631615.png" alt="image-20210819172631615" style="zoom:67%;" />
    3. 点击图上红色框<img src="https://coco-img.oss-cn-hangzhou.aliyuncs.com/img/image-20210819172709515.png" alt="image-20210819172709515" style="zoom: 67%;" />
    4. 点击图上红色框<img src="https://coco-img.oss-cn-hangzhou.aliyuncs.com/img/image-20210819172840087.png" alt="image-20210819172840087" style="zoom:67%;" />
    5. Note 可以随便写<img src="https://coco-img.oss-cn-hangzhou.aliyuncs.com/img/image-20210819173010889.png" alt="image-20210819173010889"  />
    6. token的过期时间 建议设置成无限期限![image-20210819173115385](https://coco-img.oss-cn-hangzhou.aliyuncs.com/img/image-20210819173115385.png)
    7. 为不同的用户（组）生成不同的token，给予不同的token不同的权限。自己个人用的话，全选就可以<img src="https://coco-img.oss-cn-hangzhou.aliyuncs.com/img/image-20210819173204936.png" alt="image-20210819173204936" style="zoom:80%;" />
    8. 创建token等待系统生成token<img src="https://coco-img.oss-cn-hangzhou.aliyuncs.com/img/image-20210819173240715.png" alt="image-20210819173240715"  />
    9. <font color='red'>token 记得保存好，离开页面后 将无法再看到令牌</font><img src="https://coco-img.oss-cn-hangzhou.aliyuncs.com/img/image-20210819173437351.png" alt="image-20210819173437351" style="zoom:80%;" />

    更详细的步骤 请参考官方文档：[创建个人访问令牌 - GitHub Docs](https://docs.github.com/cn/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token)

###### 推送 : 本地有仓库有内容，要推送给远程库

* <font color ='pink'>**git push -u origin master**</font>
* 第一次推送的时候 需要加上 -u 参数，Git 不但会把本地的 master 分支内容推送到远程新的 master 分支，还会把本地 master 分支和远程的 master 分支关联起来，在以后推送时可以简化命令 <font color='pink'>**git push origin master**</font>
* **备注** :  正常情况下，成功推送一次后，电脑会记住相关信息。下次推送时不会再提示输入。若电脑不能自动记住相关信息，需要执行命令 : <font color='blue'>**git config --global credential.helper store**</font>

###### 拉取 : 本地仓库有内容，获取远程库的新内容

* <font color='pink'>**git pull origin master**</font>		将远程仓库的 master 分支上的代码版本复制/合并到本地 master 分支上
* <font color='pink'>**git fetch origin master:tmp**</font>		新建一个tmp分支，将远程仓库的 master 分支上代码版本复制到本地 tmp 分支上，不会自动合并

###### 克隆 : 本地无仓库，要获取一个完整的远程库

* <font color ='pink'>**git clone 远程仓库地址**</font>

* **备注：**只在第一次获取远程库时，才需要克隆

  

# Git 常用命令总结

* **mkdir XXX		创建一个空目录  XXX指目录名**		

* **pwd		显示当前目录的路径**

* **cat xxx		查看xxx文件内容**

* <font color='red'>**git init		把当前的目录变成可以管理的 git 仓库，生成隐藏的.git 文件夹**</font>

* <font color='red'>**git add xxx		把xxx文件添加到暂存区**</font>

* <font color='red'>**git commit -m 'xxx'		提交文件 -m后面是注释 必须写**</font>

* **git status		查看仓库状态**

* **git log		查看提交历史记录**

* **git reset --hard HEAD^		往上回退一个版本**

* **git reflog		查看提交历史记录的版本号id**

* **git checkout --xxx		把xxx文件在工作区的修改全部撤销**

* **git rm xxx		删除xxx文件**

* <font color='red'>**git remote add origin https://<token令牌>@github.com/<GitHub用户名>/<仓库名> 		关联一个远程库**</font>

* <font color='red'>**git push -u ( 第一次加上 -u ，以后不用 ) origin master		把当前master分支推送到远程库**</font>

* <font color='red'>**git clone 远程仓库地址		从远程库克隆**</font>

* <font color='red'>**git checkout -b dev		创建dev分支，并切换到dev分支**</font>

* <font color='red'>**git branch		查看当前所有的分支**</font>

* <font color='red'>**git checkout master		切换回master分支**</font>

* <font color='red'>**git merge dev		在当前分支合并dev分支**</font>

* **git branch -d dev		删除dev分支**

* <font color='red'>**git branch xxx		创建分支xxx**</font>

* **git remote		查看远程库信息**

* **git remote -v		查看远程库的详细信息**

* <font color='red'>**git pull origin master		将远程库的更新拉取到本地并自动合并**</font>

  

# 提交代码的规范

* **每次提交之前：先更新，再提交**
* **敏感时间点，一定要及时更新文件**
* **多提交，避免 “只关注写代码，不关注提交” 的现象**
* **每次提交必须写清晰明了的提交说明**
* **不要提交不能通过编译的代码**
* **不要提交自己不明白的代码**
* **慎用锁定功能( 尽量避免使用锁，不轻易解锁已上锁的文件 )**
* **不要提交本地自动生成的文件、文件夹**

