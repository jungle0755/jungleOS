# jungleOS
This my os
It's Open Source of Operation System for studying.
JOS实验是MIT公开课中的一个课程，在网上很容易搜到JOS课程的网页。这个实验搭建了一个基础的OS框架，让学生一步一步地实现OS中的内存管理、中断和异常处理、environment（类似进程的概念）的创建和调度、SMP支持、文件系统等功能。难能可贵的是，代码中的注释非常清晰易懂，对于理解操作系统的实现非常有帮助。做完这个实验之后，可以对操作系统的实现有一个整体的，又不失细节的理解。

Hadware:[Paspberry Pi] The Raspberry Pi is based on the Broadcom BCM2835 system on a chip (SoC),  which includes an 700 MHz ARM1176JZF-S processor, VideoCore IV GPU,[7] and RAM.
CPU: ARM1176JZF-S 700Mhz  (ARM11 architecture  ARMv6是架构阵营)
GPU:Broadcom VideoCore IV, OpenGL ES 2.0, 1080p 30 h.264/MPEG-4 AVC
Thanks for my colleague, Lida.
ARM按阵营分为：
Ⅰ、ARMv5架构阵营，代表核心：  ARM9核心
Ⅱ、ARMv6架构阵营，代表核心：  ARM11核心
Ⅲ、ARMv7架构阵营，代表核心：  ①高通Scorpion核心      ②Cortex A8核心
                               ③三星Hummingbird核心   ④Cortex A9核心

manual: http://infocenter.arm.com/help/index.jsp

Virtual emulator: qemu on Ubuntu14.04
manual: http://qemu.weilnetz.de/qemu-doc.html

install qemu:
1.first install Qemu dependencies for Ubuntu
sudo apt-get install build-essential gcc pkg-config glib-2.0 libglib2.0-dev libsdl1.2-dev libaio-dev libcap-dev libattr1-dev libpixman-1-dev

2.install other dependencies
sudo apt-get build-dep qemu

3.then download latest Qemu source files from Download - QEMU
wget http://wiki.qemu-project.org/download/qemu-2.3.0.tar.bz2

4.extract it
sudo tar -xvjf qemu-2.3.0.tar.bz2

5.go to extracted folder
cd qemu-2.3.0/

6.compile it for 64bit (if you want 32 bit too add this ',i386-softmmu')
sudo ./configure --target-list=x86_64-softmmu,arm-softmmu  (for additional platform type  ./configure --help)
sudo make
sudo make install 

# sudo apt-get install qemu qemu-system
# qemu-system-arm --version
compile arm os:
# sudo apt-get install zlibc zlib1g zlib1g-dev sed bash dpkg-dev bison flex patch texinfo automake m4 libtool tar gzip bzip2 lzma libncurses5-dev gawk gcc-multilib g++ byacc
# mkdir -p $HOME/minix
# cd $HOME/minix
# git clone https://github.com/jungle0755/minix.git src
# cd src
# vi .settings 
# beagleboard-xm
U_BOOT_BIN_DIR=build/omap3_beagle/
CONSOLE=tty02



For beaglebone
#qemu-system-arm  -M beaglexm -drive if=sd,cache=writeback,file=minix_arm_sd.img -clock unix -serial stdio -device usb-kbd -device usb-mouse -usb

For raspberry pi
#qemu-system-arm -M versatilepb -cpu arm1176 -m 192 -hda Occidentalis_v02.img -kernel kernel-qemu -append "root=/dev/sda2" -net nic -net user,hostfwd=tcp::2222-:22,hostfwd=tcp::5800-:5800,hostfwd=tcp::5900-:5900








