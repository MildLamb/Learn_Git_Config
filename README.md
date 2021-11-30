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
