# Kali Linux 的整理

## 目录

### 安装后基本配置

#### 1. 设置kali的更新源
  > 这个源指的是软件源，也就是说你用apt-get install xxx安装软件时，系统下载软件的地方，一般默认为国外的链接，所以速度比较慢，需要换成国内的源
#### 设置kali的更新源。
> 在终端中打开sources.list
> root@kali:~# vim /etc/apt/sources.list
#### 添加更新源
#### leafpad /etc/apt/sources.list
> 删除里面的注释，清空。
> 然后输入下面的更新源地址
```
#auto
deb http://http.kali.org/kali kali-rolling main non-free contrib

#中科大
deb http://mirrors.ustc.edu.cn/kali kali-rolling main non-free contrib
deb-src http://mirrors.ustc.edu.cn/kali kali-rolling main non-free contrib

#浙大
deb http://mirrors.zju.edu.cn/kali kali-rolling main contrib non-free
deb-src http://mirrors.zju.edu.cn/kali kali-rolling main contrib non-free

#东软大学
deb http://mirrors.neusoft.edu.cn/kali kali-rolling/main non-free contrib
deb-src http://mirrors.neusoft.edu.cn/kali kali-rolling/main non-free contrib

#重庆大学
deb http://http.kali.org/kali kali-rolling main non-free contrib
deb-src http://http.kali.org/kali kali-rolling main non-free contrib

#官方源
#deb http://http.kali.org/kali kali-rolling main non-free contrib
#deb-src http://http.kali.org/kali kali-rolling main non-free contrib
``` 
>保存，保存退出，然后更新。  
```
root@kali:~# apt-get update 
root@kali:~# apt-get upgrade -y	
```

2.网络设置  
```
apt-get install pppoe pppoeconf
nm-connection-editor(DSL网络在此处添加)
```
3.输入法安装  
` apt-get install fcitx fcitx-table-wbpy `

4.字体安装  
` apt-get install ttf-wqy-microhei `

5.终端字体调整  
` Droid Sans Mono Regular ` 

6.虚拟机配置过程中内核模块未载入问题（对于64位电脑，Kali 2.0）  
```
wget kernel.ubuntu.com/~kernel-ppa/mainline/v4.3.4-wily/linux-headers-4.3.4-040304_4.3.4-040304.201601230132_all.deb  
wget kernel.ubuntu.com/~kernel-ppa/mainline/v4.3.4-wily/linux-headers-4.3.4-040304-generic_4.3.4-040304.201601230132_amd64.deb  
wget kernel.ubuntu.com/~kernel-ppa/mainline/v4.3.4-wily/linux-image-4.3.4-040304-generic_4.3.4-040304.201601230132_amd64.deb  
sudo dpkg -i linux-headers-4.3.4*.deb linux-image-4.3.4*.deb  
sudo reboot
```
7.IceWeasel汉化  
```
sudo apt-get remove iceweasel
sudo apt-get install iceweasel
sudo apt-get install iceweasel-l10n-zh-cn



系统环境： 虚拟机VMware上运行的ubuntu（linux）系统， win7系统。

解决方法：只需要在ubuntu安装一个vmware-tools的工具。

1.打开虚拟机的菜单“VM”，下拉框中会有一个Install vmware tools 工具的安装选项。
点击之后，在ubuntu的桌面下会出现 VMwareTools...tar.gz 的文件。路径（/media/VMware Tools）
2.将此文件复制到/tmp文件下进行解压
cp  VMwareTools...gz   /tmp
cd  /tmp
tar -xzvf VMwareTools...gz
3.这是会出现解压后的目录。( vmware-tools-distrib目录）。然后执行编译操作
 cd  VMwareTools...
 ./vmware-install.pl
 开始进行安装，一路回车就好了。。。
 如果无法编译，可能权限不够。可以
 sudo  ./vmware-install.pl 。如果执行过程中出现

 “...致命错误：Linux/smp_lock.h没有那个文件或目录，编译中断....”
 的错误，不用理会只管一路回车即可。

4.安装成功
Enjoy,
--the VMware team
5.重新启动ubuntu系统就行了。reboot 

OK，畅快体验吧！
```

##pycharm在kaliLinux上的安装

1、下载：
	在官网下载.tgz格式的安装压缩文件。
2、解压：
	tar zxvf  Python-3.2.2.tgz(pycharm 压缩文件名)
3、移动：
	自己的文件基本放在usr/local/**下
	mv 文件位置/ /移动到的位置/
4、执行：
	进入pycharm/bin目录下，执行pycharm.sh
	./pycharm.sh
5、软连接：
	将pycharm添加到、usr/bin 中，
   ln -s /pycharm/bin/pycharm.sh /usr/bin/pycharm
   之后每次输入pycharm就可以运行程序。
