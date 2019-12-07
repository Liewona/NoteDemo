[TOC]

# Git基本使用流程

## 1.创建Git仓库

1. `git init` 使用当前目录作为Git仓库，进行初始化
2. `git init dir` 指定dir作为Git仓库

## 2.文件纳入版本控制

使用 `git add`命令告诉Git对哪些文件进行追踪

```cmd

$ git add *.c
$ git add README
$ git commit -m "初始化项目版本"

```
上面的命令将目录下以`.c`结尾以及README文件提交到仓库中

## 添加用户名邮箱

全局
```cmd
$ git config --global user.name "github’s Name"
$ git config --global user.email "github@xx.com"
$ git config --list
```


非全局
```cmd
$ git config user.name "gitlab’s Name"
$ git config user.email "gitlab@xx.com"
$ git config --list
``

## Git克隆

```cmd
    git clone <repo>

    git clone <repo> <directory>  
```
第一个命令将git仓库中的项目克隆到当前目录
第二个命令将git仓库中的项目克隆到指定目录

<repo>  Git仓库
<directory> 本地目录

# 远程仓库

windows中，需要在 `C:\Windows\System32\drivers\etc\hosts` 中添加一行
`13.229.188.59    github.com`
<br />

作用是将github.com的ip注册到本机

```cmd
git remote add [shortname] [url]

ssh-keygen -t rsa -C "youremail@example.com"  // 生成ssh key
// windows 下在 C:\User\.ssh\id_rsa.pub文件中生成了一个key，复制到github中添加ssh验证就行

```



```cmd

$ mkdir runoob-git-test                     # 创建测试目录
$ cd runoob-git-test/                       # 进入测试目录
$ echo "# 菜鸟教程 Git 测试" >> README.md     # 创建 README.md 文件并写入内容
$ ls                                        # 查看目录下的文件
README
$ git init                                  # 初始化
$ git add README.md                         # 添加文件
$ git commit -m "添加 README.md 文件"        # 提交并备注信息
[master (root-commit) 0205aab] 添加 README.md 文件
 1 file changed, 1 insertion(+)
 create mode 100644 README.md

# 提交到 Github
$ git remote add origin git@github.com:tianqixin/runoob-git-test.git
$ git push -u origin master

```

## 查看当前远程库

`git remote ` 该命令可查看当前配置有哪些远程仓库

`git remote -v` 查看每个别名的实际链接地址


## 提取远程仓库

1、从远程仓库下载新分支与数据

```cmd
git fetch
```
该命令执行完后需要执行 `git merge`远程分支到你所在的分支。

2、从远程仓库提取数据并尝试合并到当前分支

```cmd
git merge
```

* 例如
```cmd
git fetch origin

git merge origin/master

```

3、还可以通过以下命令下载远程仓库中的数据
```cmd
git pull origin master
```

## 推送到远程仓库

```cmd
git push [alias] [branch]
```
上述命令将[branch]分支推送成为[alias]远程仓库上叼[branch]分支

```cmd

$ touch runoob-test.txt      # 添加文件
$ git add runoob-test.txt 
$ git commit -m "添加到远程"
master 69e702d] 添加到远程
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 runoob-test.txt

$ git push origin master    # 推送到 Github

```

### 防止每次push都输入密码
在push和pull之前输入该参数，生成记录文件记录账号密码，下次就不需要输入了
```cmd
git config --global credential.helper store
```

## 删除远程仓库

```cmd
git remote rm [别名]
```
* 例如
```cmd

$ git remote -v
origin    git@github.com:tianqixin/runoob-git-test.git (fetch)
origin    git@github.com:tianqixin/runoob-git-test.git (push)

# 添加仓库 origin2
$ git remote add origin2 git@github.com:tianqixin/runoob-git-test.git

$ git remote -v
origin    git@github.com:tianqixin/runoob-git-test.git (fetch)
origin    git@github.com:tianqixin/runoob-git-test.git (push)
origin2    git@github.com:tianqixin/runoob-git-test.git (fetch)
origin2    git@github.com:tianqixin/runoob-git-test.git (push)

# 删除仓库 origin2
$ git remote rm origin2
$ git remote -v
origin    git@github.com:tianqixin/runoob-git-test.git (fetch)
origin    git@github.com:tianqixin/runoob-git-test.git (push)
```
# 当本地仓和远程仓认为不是统一仓库时

后面添加参数可使强制合并

使用:
```cmd
git pull origin master --allow-unrelated-histories
```
# 注

* 执行 git fetch origin master 时，它的意思是从名为 origin 的远程上拉取名为 master 的分支到本地分支 origin/master 中。既然是拉取代码，当然需要同时指定远程名与分支名，所以分开写。
* 执行 git merge origin/master 时，它的意思是合并名为 origin/master 的分支到当前所在分支。既然是分支的合并，当然就与远程名没有直接的关系，所以没有出现远程名。需要指定的是被合并的分支。
* 执行 git push origin master 时，它的意思是推送本地的 master 分支到远程 origin，涉及到远程以及分支，当然也得分开写了。
* 还可以一次性拉取多个分支的代码：git fetch origin master stable oldstable；
* 也还可以一次性合并多个分支的代码：git merge origin/master hotfix-2275 hotfix-2276 hotfix-2290；

