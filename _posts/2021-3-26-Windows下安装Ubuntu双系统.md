Ubuntu20.04现在网上一般说有很多的Bug，相对而言18.04比较稳定些，因此本次安装选择的Ubuntu的版本为18.04，用的磁盘刻录工具为rufus
## 工作站硬件配置
- 处理器 至强E5
- 显卡 四张1080ti
- 硬盘 一张1T固态，一张8T机械
一般将固态作为系统引导盘，机械作为数据盘，因此固态盘需要分出一部分来装Ubuntu。同时，C盘前有个500M保留分区，因此系统为传统模式安装而非UEFI模式，在安装时也应选择传统模式安装而不是UEFI
## 安装流程
- 下载镜像文件
- 刻录U盘
- 选择从U盘启动（选择不带UEFI的那个U盘，之前选择带UEFI前缀的导致点击安装后一直黑屏）
- 双击固态盘的空闲磁盘，选择挂载点为‘/’，双击机械硬盘的空闲磁盘位置，选择挂在点为‘/home’（其他的不用管）
- 引导位置选择为固态盘（整个盘而不是固态盘的某个分区）
- 安装Ubuntu
## 安装显卡驱动
### 去Nvidia官网下载最新的相应显卡驱动，并改名‘1080ti.run’
### 将下载好的驱动放到主目录下，即放置‘下载’文件夹的那个目录
### 屏蔽开源驱动nouveau
- sudo gedit /etc/modprobe.d/blacklist.conf
- 加参数到最底下，回车另起一行，内容为：blacklist nouveau
- options nouveau modeset=0
- 保存再终端内更新内核命令
- sudo update-initramfs -u
- sudo apt update
- sudo apt install gcc g++ make
- 重启电脑
### 安装新驱动程序
- 重启后Ctrl + Alt + F3到控制台，'sudo telinit 3'关闭当前图形环境（或者启动时选择Ubuntu高级设置启动）
-  选择recovery mode
-  选择root
- 进入主文件夹即home文件夹下，‘cd /home/用户名’（忘记用户名可以使用‘ls’命令来显示当前文件夹下的内容）
- sudo chmod a+x 1081ti.run
- sudo sh 1080ti.run -no-opengl-files
- ‘reboot’重启命令即可
- 重启后命令行使用‘nvidia-smi’命令可查看显卡状态
