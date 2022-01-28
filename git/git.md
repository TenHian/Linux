# linux下git配置
## 安装
```shell
sudo apt-get install git
```
## 配置git用户
<font size=4>配置用户</font>  

```shell
git config --global user.name "git的用户名"
git config --global user.email "git的邮箱"
```
<font size=4>配置SSH用户</font>  
1. 生成密钥  

   ```shell
    ssh-keygen -t rsa -C "git的邮箱"
   ```  

2. 查看密钥  

   ```shell
    cat /home/tenhian/.ssh/id_rsa.pub
   ```
3. 在github->settings->SSH and GPG keys新建SSH key,将前面的密钥复制到key栏，title可随意，只要能区分不同的SSH key  

<font size=4>检测SSH用户是否可用</font>  
```shell
ssh -T git@github.com
```
<font size=4>注：配置SSH用户后，git push命令可直接对远程的ssh源仓库修改，不用输入用户名密码；如是远程https的，可使用一下命令替换远程仓库类别为SSH类型,SSH链接在github你的repository的code按钮</font>   
![github-code](https://raw.githubusercontent.com/TenHian/picbed/master/Linux/github-code.png?token=AN2ABMESXOLWGDV7T5IWO5TB6PHNU)

```shell
git remote -v  #查看当前使用的远程仓库类别
git remote rm origin
git remote add origin 复制的SSH #SSH例：git@github.com:TenHian/Linux.git
```  

# git介绍与使用
## 关于git
<font size=4>git是一个分布式版本控制软件，最初由Linus Torvalds创作，于2005年以GPL许可协议发布。最初目的是为了更好地管理Linux内核开发而设计。</font>  

## git基本组成框架
+ workspace
+ index/stage
+ repository
+ remote   

<font size=4>workspace:工作区;是开发者在本地存放代码的目录。在只有一人的开发团队中，workspace总是保存最新版本的代码。<br>index/stage:暂存区;最新版本git中为index，用于存放临时动作，可撤销<br>repository:仓库;特指本地仓库，`git commit`命令就是将暂存区的修改提交到仓库中，在分布式git工作流程中，repository有时是workspace，存放着每个开发者相对成熟的代码。由于分布式，每个开发者的repository都可以是主版本。<br>remote:远程仓库;非本地仓库。在具体工作中，一般是多个开发者开发一个项目，远程仓库是每个开发者将本地repository提交到的地方，是整合各个开发者贡献的地方。常见的remote服务提供商有github、gitee、Azure等。</font>  

## 分布式与分支