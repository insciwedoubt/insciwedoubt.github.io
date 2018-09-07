SU安装教程
====
(时间：2017-12；系统：Ubuntu 16.04）  

### 1. 下载安装包与准备安装

* 官网下载安装包  
CWP官网：<http://www.cwp.mines.edu/cwpcodes/index.html>

* 阅读Installation Instruction  
在安装包里有安装的教程。依照提示操作就可以安装。

* 移动压缩包到指定文件夹
```Bash
		$ mv {原目录}/{压缩包名} {新目录}
```

* 解压缩：
```Bash
		$ tar -xvzf {压缩包名}
		$ tar -xvzf {压缩包名} -C {目标地址}
```

* **解压完成后得到src文件夹。以下安装到目录`/home/user/su`下。**  
你可以将目录替换成你的安装目录，并注意将以下命令一并修改。

### 2. 设置环境变量

* 用户目录`/home/user`，用vim打开.bashrc文件：  
```Bash
	$ vim .bashrc
```

* 在底部加入代码：  
```Bash
	export CWPROOT=/home/user/su
	export PATH=$PATH:/home/user/su/bin
```
* 保存，回到终端，确认更改：  
```Bash
	$ source .bashrc
```

* 查看环境变量设置是否成功：  
```Bash
	$ echo $CWPROOT
	$ echo $PATH
```

### 3. 配置安装SU前置软件包

* 用户目录`/home/user`打开终端，输入命令：  
```Bash
	$ sudo apt install bulid-essential
	$ sudo apt install libxt-dev
	$ sudo apt install libx11-dev
	$ sudo apt install libxmu-dev
	$ sudo apt install libxi-dev
	$ sudo apt install gfortran
	
	$ sudo apt install freeglut3-dev
```
* 使用替代libglut3的软件包。  
	在Ubuntu 10.04版本以后，找不到软件包libglut3，使用freeglut3作为替代。已在上方命令中替换。  

**参考问题解决：**  
	1. <https://askubuntu.com/questions/332375/unable-to-locate-package-libglut3-dev>  
	2. <http://blog.csdn.net/jarvischu/article/details/8226938>  

### 4. 安装SU

* 终端，进入`/home/user/su/src`文件夹，执行命令：  
```Bash
	$ make install
	$ make xtinstall
	$ make finstall
	$ make mglinstall
```

* 可选项，可选择安装：  
```Bash
	$ make xminstall		（可安装）
	$ make utils			（可安装）
```

### 5. 测试安装
会出现一个图像  
```Bash
	$ suplane |  suxwigb &
```

### 6. 常见问题

* **Makefile:32 /src/Makefile.config: 没有那个文件或目录**  
	应该是CWPROOT的设置问题，注意使用绝对路径时的符号。  
	如果不是这个问题，也可以考虑重新解压缩。  

* **未找到命令**  
	可能是环境变量设置问题，设置的环境变量中搜索不到命令。  
	设置环境变量时注意符号，可以用echo命令查看当前环境变量路径进行确认。   

* **文件夹权限不够**  
	提高文件夹权限，777是最高权限。不过过高权限会有一定风险。  
	命令如下：  	
```Bash
	$ sudo chmod 777 /home/user/su
```

* **修改/home/user/su/Makefile.config**  
	最新版本中无此类问题。出现问题可查看参考教程链接。  

### 7. 参考教程

1. <http://www.educity.cn/os/1577183.html>
2. <http://any2sky.blog.163.com/blog/static/46851803200993011193544/>
3. <http://blog.sina.com.cn/s/blog_49b09fb10100076q.html>

