## step1. git安装

1.apt-get install git

2.配置git账号：git config --global user.name "your name"

​                           git config --gloabal user.email "your email address"

3.生成SSH密钥：ssh-keygen -t rsa -C "your email address"

然后会提示选择密钥的保存路径，直接回车选择默认路径就好

4.去到刚刚保存密钥的路径，cat /home/user/.ssh/id_rsa.pub（可以先去那个路径确认一下是否正确生成了密钥），打开生成密钥后复制（不复制最后的邮箱），然后添加到GitHub账号中的密钥，就可以正确使用啦～

## step2. git使用

### 一. 将一个本地项目上传至GitHub

（一）第一种方式

1.在GitHub上首先新建一个新的仓库；

2.在本地进入一个文件夹，然后git clone 地址，将远程仓库拉到本地。

3.在本地文件夹中将待上传的项目放到该文件夹中，然后git add .，将所有文件加入到暂存区，然后git commit -m "information"提交，最后git push -u origin master，将暂存区的这些信息都上传至远程仓库。

（二）第二种方式

1.在github先新建一个空的仓库；

2.本地已有该项目，进到该路径下，然后git init在本地初始化一个仓库，然后git add .将所有内容添加，接着git commit -m "info"将所有内容提交；

3.git git remote add origin sample.git(github上的仓库地址)，将本地仓库与远程仓库相连

4.git push -u origin master

### 二. 远程更新之后，将更新内容同步到本地

若是远程仓库中的内容有变化，那么在本地通过git pull，这样默认从远程仓库中拉回有更新的地方

### 三. 若是本地项目有更新，将其同步到远程仓库

1.git status查看目前的状态，有哪些更新了

2.git add -u，update，即将已经被track的所有文件的更新内容提交至缓存区，然后后续相同的操作，即git commit -m "",git push -u origin master.

### 四. 几种不同的将修改内容提交至缓存区

**git add . ：**会监控工作区的状态树，使用它会把工作时的**所有变化提交**到暂存区，包括文件内容**修改**(modified)以及**新文件**(new)，但**不包括被删除**的文件。

**git add -u** **：**他仅监控**已经被add的文件**（即tracked file），他会将**被修改**的文件提交到暂 存区。add -u **不会提交新文件**（untracked file）。（git add --update的缩写）

**git add -A** **：**是上面两个功能的合集（git add --all的缩写）

### 五. 一些多人协作的应用场景

1.多人协作，或者修改一些内容需要新开分支：

git checkout -b branchname：新建一个分支，在这个分支上修改提交。

git add .

git commit -m "information"

git push origin branchname:pengpeng/originbranchname：将本地分支的这次修改提交到远程服务器上的一个新分支，在review后再与master分支进行merge操作，再把当前的这个旁分支删除掉。

2.多人协作，但是review时代码需要再次修改时：

修改代码后，在commit时不要新建一个commit信息，可使用git commit --amend --no-edit，这样就是在上次的commit后进行追加，这样操作之后再push到远程服务器上的分支上，经过review后再与master进行merge。

3.多人同时修改项目文件时，如果提交时master分支已经更新过了。

这时先git add和git commit，然后再git pull --rebase，将本地的项目更新到最新，并与自己当前修改的进行了合并，然后再push，这样的话自己修改的代码就是在目前最新的代码上进行修改的了。

4.git log --graph查看当前的所有分支的情况（以图的形式）

git log查看所有的commit信息，然后可以根据commit的编号，checkout到你想要的那份代码上。