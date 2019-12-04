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