# Learn_Git_Config
使用git远程配置

# git 环境搭建

## git生成SSH公钥命令
- 在你的C:\Users\MildLamb\.ssh文件夹下，git bash
- 输入命令
```bash
$ ssh-keygen -t rsa -C "1902524390@qq.com"
```
- 回车 回车 回车，就会生成两个文件
  - id_rsa和id_rsa.pub
- 把id_rsa.pub添加到github的ssh里面
- clone这个项目，可以使用https或者ssh
- clone后，在对应文件夹中编写一个application.yml文件
```yml
spring:
  profiles:
    active: dev

---
spring:
  profiles: dev
  application:
    name: springcloud-config-dev

---
spring:
  profiles: test
  application:
    name: springcloud-config-test
```
- 将编写的yml文件，提交到GitHub
  - 在项目目录中git bash
  - 添加修改的文件
```bash
$ git add .
```
  - 查看暂存区状态
```bash
$ git status
```
  - 将文件添加到本地
```bash
$ git commit -m "first commit"
```
  - 将文件提交到远程
```bash
$ git push origin main
```
## 遇到的一些小问题
error: failed to push some refs to 'github.com:MildLamb/Learn_Git_Config.git'  
原因，我在github修改文件的同时，想要用git远程修改，导致冲突  
解决办法：
- 先使用命令
```bash
$ git pull --rebase origin main
```
这条指令的意思是把远程库中的更新合并到本地库中，–rebase的作用是取消掉本地库中刚刚的commit，并把他们接到更新后的版本库之中。


# Git 分支操作
1. 克隆项目分支
在工作目录下使用 git clone -b branchName reposURL 下载项目名为 branchName 的分支。  

2. 添加更改
将需要更改的文件进行更改，这样得到一个更新后的原项目，之后进入项目根目录，使用 git add . 命令更新全部。  

3. 确认提交
使用 git commit -m comment 确认提交，其中 comment 可以换成任意文字作为提交时的注释。  

4. 创建分支（optional）
如果新开一个 branch 可以使用 git branch branchName 创建一个名为 branchName 的新分支，如果 branchName 分支已存在则该条命令会报错。  

5. 切换分支
使用 git checkout branchName 将目标分支更改为 branchName。  

6. 更新分支
使用 git push origin branchName 进行更新，如果是单独创立的文件夹（不是通过 git clone 下载的）需要在 push 之前先使用 git remote add origin reposURL 命令与远程仓库进行关联。


PS：该步骤可能需要用户认证，需要输入用户名和密码，如果之前已经设置过 SSH 密钥则不再需要用户验证。一般情况默认 git clone 的时候已经输入过一遍了，所以这里可以直接上传。在目前版本的 GitHub 中，会使用 main 作为默认 branch 的名称，所以需要将名称先改为 master 从而避免之后 branch 合并分叉问题
