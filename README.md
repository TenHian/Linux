# 基本上手

## 换源
### Ubuntu换源
<font size=4>备份已有源<br>
`sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup`<br>
打开源列表文件<br>
`sudo nano /etc/apt/sources.list`<br>
将其中内容注释掉或删除<br>
改为:</font>

```
deb http://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse
```
<font size=4>然后<br>`sudo apt update`<br>`sudo apt upgrade`</font>

### Kali换源
```
deb http://mirrors.aliyun.com/kali kali-rolling main non-free contrib
deb-src http://mirrors.aliyun.com/kali kali-rolling main non-free contrib
```

### CentOS8换源
<font size =4>备份：</font>

```
sudo cp -r /etc/yum.repos.d/ /home/tenhian/
```

<font size =4>删除已有源</font>

```
sudo rm -r /etc/yum.repos.d/
```

<font size =4>重新下载新源</font>

```
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-8.repo
```

<font size =4>生成缓存</font>

```
yum makecache
```
## debian换源
```
deb http://mirrors.ustc.edu.cn/debian stable main contrib non-free
deb http://mirrors.ustc.edu.cn/debian stable-updates main contrib non-free
```


## 安装vmtools

```
第一行命令：sudo apt-get upgrade
第二行命令：sudo apt-get install open-vm-tools-desktop -y
第三行命令：sudo reboot
```

 

## 设置root用户密码

```
sudo passwd root
```



## nano的使用

<font size=4>vim和nano同是文本编辑器，我更倾向于使用nano，因为有提示</font>



## Vim

### 显示行号

<font size=4>在命令模式下<br>`:set number`</font>

### VIM与系统剪贴板的复制粘贴

#### 前提

<font size=4>开始前需要先查看`vim`是否已经支持`clipboard`功能，使用`vim --version | grep clipboard`命令查看，已经支持时其前有`+`号</font>

![image-20210809010825789](https://gitee.com/teng-huaian/picupload1/raw/master/kali/image-20210809010825789.png)

<font size=4>如果其前为`-`号，执行`sudo apt install vim-gtk`安装`vim-gtk`即可，安装完成后再执行`vim --version | grep clipboard`此时应该已经支持`clipboard`功能。</font>

#### 配置

<font size=4>此时如果在`vim`外复制了文本，要粘贴到打开的`vim`文件内，只需在`normal模式下`（如果不知道当前在哪个模式就先按一次`ESC`键）执行`"*p`<br>类似的，要将`vim`中的数据复制到`vim`外，需要回到`normal`模式先按`v`进入`visual`模式，移动光标选中目标文本后，在`visua模式下`执行`"` `+` `y`即可将`vim`数据复制到系统剪贴板，在`vim`外执行`Ctrl V`即可完成数据粘贴。</font>

### vim 使用详解

[linux下vim的使用](https://blog.csdn.net/yangshuainan/article/details/78219604?ops_request_misc=%7B%22request%5Fid%22%3A%22162900276416780262587042%22%2C%22scm%22%3A%2220140713.130102334..%22%7D&request_id=162900276416780262587042&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-78219604.first_rank_v2_pc_rank_v29&utm_term=vim&spm=1018.2226.3001.4187)

## Kali自带的截屏功能

<font size=4>全屏：PrintScreen<br>区域截图：shift + PrintScreen</font>

## 删除、安装、更换内核

### 查看当前正在使用的内核

```
uname -a
```

### 查看还有那些内核

```
dpkg --get-selections | grep linux 
```

### 删除多余的内核文件

```
sudo apt-get purge linux-headers-<版本号> 
sudo apt-get purge linux-image-<版本号>-generic 
```

<font size=4>若安装或更新内核则改为</font>

```
sudo apt-get install linux-image-<版本号>-generic linux-headers-<版本号>-generic
```

### 更新grub文件

```
sudo update-grub 
```

## 下载并配置plank

### 安装plank

```
sudo apt-get install plank
```

### 在Tweak中startup加入plank

![img](https://gitee.com/teng-huaian/picupload1/raw/master/kali/20200821153507102.png)

### 关闭Ubuntu自带的Ubuntu Dock

```
sudo apt remove gnome-shell-extension-ubuntu-dock
```

<font size=4>下载mcOS_Mojave.zip</font>

https://www.gnome-look.org/p/1248226/

<font size=4>移动</font>

```
unzip -qq mcOS_Mojave.zip
mv mcOS_Mojave\ /home/.local/share/plank/themes
```

### 重启

# 各种软件的安装

## DOSBOX汇编环境搭建

```shell
sudo apt-get install dosbox

 

cd .dosbox

dir

nano dosbox-0.74-3.conf  //打开.conf文件，在文末加如下代码

mount c /home/tenhian/masm

c:
```

## sublime text3 安装

<font size=4>1.Install the GPG key:</font>

​	`wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -`

<font size=4>2.Ensure apt is set up to work with https sources:</font>

​	`sudo apt-get install apt-transport-https`

<font size=4>3.Select the channel to use:</font>

<font size=3>	Stable:</font>

​		`echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list`

​	<font size=3>Dev:</font>

​		`echo "deb https://download.sublimetext.com/ apt/dev/" | sudo tee /etc/apt/sources.list.d/sublime-text.list`

<font size=4>4.Update apt sources and install Sublime Text</font>

​	`sudo apt-get update`

​	`sudo apt-get install sublime-text`



## Kali配置proxychains实现科学上网

### 说明

<font size=4>虚拟机网络模式应为 桥接模式 <br>物理机应运行代理软件，但不需要开启代理</font>

### 安装proxychains

<font size=4>安装下载源码</font>

`git clone https://github.com/rofl0r/proxychains-ng`

<font size=4>编译和安装 root下</font>

```
cd proxychains-ng
./configure --prefix=/usr --sysconfdir=/etc
make
make install
make install-config
cd ..
rm -rf proxychains-ng
```

### 修改配置文件

`vim /etc/proxychains.conf`

<font size=4>去掉 dynamic_chain 前面的 # <br>文件末尾</font>

```
[ProxyList]
# add proxy here ...
# meanwile
# defaults set to "tor"
socks4 	127.0.0.1 7890
socks5  192.168.0.3 7890
```

<font size=4>sock4的端口号和sock5的端口号相同，相同与物理机代理软件的端口号，sock5的IP为物理机IP</font>

### 安装并配置tor

`sudo aptitude install tor`

```
service tor status	//查看tor运行状态
service tor start	//启动tor服务
service tor stop	//停止tor服务
```

<font size=4>service tor 启动后就可执行类似命令</font>

`proxychains firefox`

<font size=4>此时firefox已经可以科学上网了</font>

### 设置tor开机自启

<font size=4>因为tor是服务，所以将tor服务设置为开机自启，使用命令:</font>

```
sudo update-rc.d tor enable
```

<font size=4>重启</font>

## 另一种道路----clashy

### 下载

[Releases · SpongeNobody/Clashy · GitHub](https://github.com/SpongeNobody/Clashy/releases)

## Kali配置Nessus实现漏洞扫描

### Nessus下载与安装

<font size=4>nessus下载网址:</font>

https://www.tenable.com/downloads/nessus?loginAttempted=true

由于我的系统为Kali Linux

## Kali安装中文输入法

### 安装输入法框架

`apt-get install fcitx`

### 安装谷歌输入法

`apt-get install fcitx-googlepinyin`

<font size=4>重启</font>

## 安装VScode
<font size=4>访问官网下载安装：</font>
https://code.visualstudio.com/

## 安装chrome
<font size=4>1.访问chrome主页下载对应系统版本的deb安装包:</font>
https://www.google.com/chrome/

<font size=4>2.安装</font>

```
dpkg -i 下载的deb
```
<font size=4>3.添加命令行启动方式</font>
```
vim /opt/google/chrome/google-chrome
```
<font size=4>将最后一行改为:</font>
```
exec -a "$0" "$HERE/chrome" "$@" --user-data-dir --no-sandbox
```
## zsh以及oh-my-zsh配置

### 查看当前shell

```
echo $SHELL
```

### 查看系统已经安装的shell

```
cat /etc/shells
```

### 安装zsh

```
sudo apt-get update
sudo apt-get install zsh
```

### 将默认shell改为zsh

```
chsh -s /bin/zsh
```

<font size=4>安装下面安装需要的组件</font>

```
sudo apt install curl
sudo apt install git
sudo apt install vim
```

### 安装oh-my-zsh

```
sh -c "$(curl -fsSL https://gitee.com/shmhlsy/oh-my-zsh-install.sh/raw/master/install.sh)"
```

### 安装插件

<font size=4>自动补全插件</font>

```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh}/plugins/zsh-autosuggestions
```

<font size=4>语法高亮插件</font>

```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh}/plugins/zsh-syntax-highlighting
```

<font size=4>autojump自动跳转插件</font>

```
sudo apt-get install autojump
```

<font size=4>对以上三者进行配置</font>

```
vim ~/.zshrc
```

<font size=4>ZSH_THEME这一行改为(单纯因为ys这个主题比较合我的口味)</font>

```
ZSH_THEME="ys"
```

<font size=4>plugins这一行改为（使前两个插件生效）</font>

```
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

<font size=4>最后一行加上 （使自动跳转插件生效）</font>

```
. /usr/share/autojump/autojump.sh
```

### 使配置生效

```
source ~/.zshrc
```

<font size=4>重启</font>



## 安装typroa

```
# or run:
# sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE

wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -

# add Typora's repository

sudo add-apt-repository 'deb https://typora.io/linux ./'

sudo apt-get update

# install typora

sudo apt-get install typora
```

### 配置typora图床

<font size=4>首先安装 npm </font>

```
sudo apt-get install npm
```

<font size=4>再如图设置</font>

![image-20210809004727853](https://gitee.com/teng-huaian/picupload1/raw/master/kali/image-20210809004727853.png)

<font size=4>点击下载或更新，下载完毕后，点击验证图片上传选项</font>

![image-20210809005304773](https://gitee.com/teng-huaian/picupload1/raw/master/kali/image-20210809005304773.png)

<font size=4>得知其安装位置，安装两个插件</font>

```
cd /home/tenhian/.config/Typora/picgo/linux/
./picgo install gitee-uploader 
./picgo install super-prefix
```

<font size=4>修改配置文件为：</font>

```
{
  "picBed": {
    "uploader": "gitee",
    "current": "gitee",
    "gitee": {
      "branch": "master",	//上传分支，默认master
      "customPath": "",
      "customUrl": "",
      "path": "kali/",		//上传存储的路径
      "repo": "teng-huaian/picupload1/image",		//仓库名
      "token": "da632a31412bc1e536ab94a5adb5b530"	//token
    }
  },
  "picgoPlugins": {
    "picgo-plugin-gitee-uploader": true,
    "picgo-plugin-super-prefix": true
  },
  "picgo-plugin-gitee-uploader": {
    "lastSync": "2021-08-09 12:53:08"
  }
}
```

<font size=4>此时已能上传<br>另外附上一个比较喜欢的主题</font>

# Ubuntu的各种命令

## ifconfig命令

[ifconfig 命令详解_一个人的旅行的博客-CSDN博客_ifconfig](https://blog.csdn.net/u011857683/article/details/83758503?ops_request_misc=%7B%22request%5Fid%22%3A%22162579885816780357214976%22%2C%22scm%22%3A%2220140713.130102334..%22%7D&request_id=162579885816780357214976&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-83758503.first_rank_v2_pc_rank_v29_1&utm_term=ifconfig&spm=1018.2226.3001.4187)

## aptitude -- Debian Linux系统中包管理工具
<font size=4>aptitude 命令与apt-get命令一样，但aptitude在处理依赖问题上更佳一些</font>

### 语法

```
aptitude <选项> <参数>
```

### 选项

```
-h：显示帮助信息；
-d：仅下载软件包，不执行安装操作；
-P：每一步操作都要求确认；
-y：所有问题都回答“yes”；
-v：显示附加信息；
-u：启动时下载新的软件包列表。
```

### 常用实例

```
aptitude update            # 更新可用的包列表
aptitude upgrade           # 升级可用的包
aptitude dist-upgrade      # 将系统升级到新的发行版
aptitude install pkgname   # 安装包
aptitude remove pkgname    # 删除包
aptitude purge pkgname     # 删除包及其配置文件
aptitude search string     # 搜索包
aptitude show pkgname      # 显示包的详细信息
aptitude clean             # 删除下载的包文件
aptitude autoclean         # 仅删除过期的包文件
```

## apt-get

### 选项

```
apt-get install 安装新包
apt-get remove 卸载已安装的包（保留配置文件）
apt-get purge 卸载已安装的包（删除配置文件）
apt-get update 更新软件包列表
apt-get upgrade 更新所有已安装的包
apt-get autoremove 卸载已不需要的包依赖
apt-get dist-upgrade 自动处理依赖包升级
apt-get autoclean 将已经删除了的软件包的.deb安装文件从硬盘中删除掉
apt-get clean 删除软件包的安装包

-c：指定配置文件。
```

## dpkg

### 说明

<font size=4>**dpkg命令** 是Debian Linux系统用来安装、创建和管理软件包的实用工具。</font>

### 实例

```
dpkg -i package.deb     # 安装包
dpkg -r package         # 删除包
dpkg -P package         # 删除包（包括配置文件）
dpkg -L package         # 列出与该包关联的文件
dpkg -l package         # 显示该包的版本
dpkg --unpack package.deb  # 解开deb包的内容
dpkg -S keyword            # 搜索所属的包内容
dpkg -l                    # 列出当前已安装的包
dpkg -c package.deb        # 列出deb包的内容
dpkg --configure package   # 配置包
```

# Ubuntu出的一些问题
## Kali使用不了 add-apt-repository 命令
<font size=4>安装 software-properties-common </font>
`apt-get install software-properties-common`

# 服务器配置



# xshell快捷键

[xshell的快捷键（非常实用） - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/105280992)



