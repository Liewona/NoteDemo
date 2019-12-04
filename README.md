# Git����ʹ������

## 1.����Git�ֿ�

1. `git init` ʹ�õ�ǰĿ¼��ΪGit�ֿ⣬���г�ʼ��
2. `git init dir` ָ��dir��ΪGit�ֿ�

## 2.�ļ�����汾����

ʹ�� `git add`�������Git����Щ�ļ�����׷��

```cmd

$ git add *.c
$ git add README
$ git commit -m "��ʼ����Ŀ�汾"

```
��������Ŀ¼����`.c`��β�Լ�README�ļ��ύ���ֿ���

## Git��¡

```cmd
    git clone <repo>

    git clone <repo> <directory>  
```
��һ�����git�ֿ��е���Ŀ��¡����ǰĿ¼
�ڶ������git�ֿ��е���Ŀ��¡��ָ��Ŀ¼

<repo>  Git�ֿ�
<directory> ����Ŀ¼

# Զ�ֿ̲�

windows�У���Ҫ�� `C:\Windows\System32\drivers\etc\hosts` �����һ��
`13.229.188.59    github.com`
<br />

�����ǽ�github.com��ipע�ᵽ����

```cmd
git remote add [shortname] [url]

ssh-keygen -t rsa -C "youremail@example.com"  // ����ssh key
// windows ���� C:\User\.ssh\id_rsa.pub�ļ���������һ��key�����Ƶ�github�����ssh��֤����

```



```cmd

$ mkdir runoob-git-test                     # ��������Ŀ¼
$ cd runoob-git-test/                       # �������Ŀ¼
$ echo "# ����̳� Git ����" >> README.md     # ���� README.md �ļ���д������
$ ls                                        # �鿴Ŀ¼�µ��ļ�
README
$ git init                                  # ��ʼ��
$ git add README.md                         # ����ļ�
$ git commit -m "��� README.md �ļ�"        # �ύ����ע��Ϣ
[master (root-commit) 0205aab] ��� README.md �ļ�
 1 file changed, 1 insertion(+)
 create mode 100644 README.md

# �ύ�� Github
$ git remote add origin git@github.com:tianqixin/runoob-git-test.git
$ git push -u origin master

```