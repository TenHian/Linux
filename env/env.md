# Linux中的环境变量
## 有关环境变量的命令
### env
<font size=4>`env`命令打印系统全部环境变量，这些环境变量来自于`/etc/environment /etc/profile ~/.bashrc`等等</font>
### export
<font size=4>`export`命令为shell变量或函数设置导出属性</font>  
<font size=4>**作用**:</font>  
<font size=4>为当前shell定义一个环境变量，该环境变量是暂时的，会在当前shell关闭后失效(并不保存在文件中)</font>  
<font size=4>**选项**:</font>  
```
-f：指向函数。
-n：删除变量的导出属性。
-p：显示全部拥有导出属性的变量。
-pf：显示全部拥有导出属性的函数。
-nf：删除函数的导出属性。
--：在它之后的选项无效。
```  
<font size=4>**例子**:</font>  
<font size=4>设置http代理;这里导出了`http_proxy`这个变量，使之成为了一个暂时的环境变量</font> 
```shell
export http_proxy=http://127.0.0.1:7890/
```  
## 有关环境变量的文件
### 系统级
`/etc/profile`  
<font size=4>在系统启动后第一个用户登录时运行，并从`/etc/profile.d`目录的配置文件中搜集shell的设置，使用该文件配置的环境变量将应用于登录到系统的每一个用户，只获取一次</font>  
`/etc/bashrc` Debian系中是 `/etc/bash.bashrc`  
<font size=4>在 bash shell 打开时运行，修改该文件配置的环境变量将会影响所有用户使用的bash shell</font>  
`/etc/environment`  
<font size=4>在系统启动时运行，用于配置与系统运行相关但与用户无关的环境变量，修改该文件配置的环境变量将影响全局</font>
### 用户级
`~/.profile`  
<font size=4>当用户登录时执行，每个用户都可以使用自己的该文件来配置专属于自己使用的shell信息</font>  
`~/.bashrc`
<font size=4>配置自己的bash shell信息，每打开一个bash shell便读取一边</font>  
`~/.bash_profile  ~./bash_login`(选读)  
<font size=4>`~/.bash_profile` or `~./bash_login` - If one of these file exist, bash executes it rather then `~/.profile`<br>when it is started as a login shell. (Bash will prefer `~/.bash_profile` to `~/.bash_login`).<br>However, these files won't influence a graphical session by default.</font>  
`~/.bash_logout`  
<font size=4>退出bash shell时读取</font>