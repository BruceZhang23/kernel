# kernel
vim /etc/sysctl.conf


lsmod | grep floppy
modprobe    装载模块
modprobe -r floppy 卸载
/lib/modules

modinfo floppy 查看模块具体信息   查看路径
modinfo pcnet32
modinfo mii

insmod /path/modulefile
rmmod Name
depmod /path/modulefile

devloptools


tar xf linux-2.6.28.10.tar.gz -C /usr/src
ln -sv linux-2.6.28.10 linux
cd linux
make menuconfig
ls ./config
make modules_install
make install

screen命令：
screen -ls: 显示已经建立的屏幕
screen: 直接打开一个新的屏幕
	Ctrl+a, d: 拆除屏幕
screen -r ID: 还原回某屏幕
exit: 退出


二次编译时清理，清理前，如果有需要，请备份配置文件.config：
make clean
make mrproper

grub-->kernel-->initrd-->ROOTFS(/sbin/init, /bin/bash)

gzip -d inittd-2.6.18-308.el5.img.gz
cpio -id < ../inittd-2.6.18-308.el5.img
或 zcat /boot/inittd-2.6.18-308.el5.img | cpio -id



编译内核：
1、配置
make menuconfig
make gconfig
make kconfig
make oldconfig
make config

保存为.config

2、
make
make modules_install
make install
	
模块安装位置：/lib/modules/KERNEL_VERSION/	
	

如何实现部分编译：
1、只编译某子目录下的相关代码：
make dir/

make arch/
make drivers/net/

2、只编译部分模块
make M=drivers/net/

3、只编译某一模块
make drivers/net/pcnet32.ko

4、将编译完成的结果放置于别的目录中
make O=/tmp/kernel 

5、交叉编译
make ARCH=
