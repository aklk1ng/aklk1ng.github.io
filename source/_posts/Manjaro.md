---
title: Manjaro
---
# Manjaro双系统的安装与简易配置

### 1.首先是iso镜像的下载，可以前往以下地址：

https://manjaro.org/download/

**对于下载而言，官网提供了三种发行版，可以自行选择，再可以选择Torrent文件再使用相应软件（windows微软商店可以搜索）进行完整的下载，也可以直接下载iso文件**

### 2.U盘启动盘的制作，在windows中下载Rufus软件，具体的选择可以参考下图：

![](.//Manjaro/v2-47a5018309090d6cdaf35f1b4f3190f4_r.jpg)

### 3.安装系统前的准备

* 在windows系统中要关闭系统的安全启动模式
* 对现有的磁盘进行分区来给Manjaro提供空间，我的空间是100g,如果仍有余地的话可以再加
* 对于windows系统可以在系统设置里找到**系统更新**，再找到**恢复**，最后是**高级启动**，这样可以在启动时提供使用U盘进行引导的选择，也可以使用通用方法：进入bios模式（具体笔记本可以自查），将U盘启动项提高至优先级

### 4.正式安装

当你成功选择U盘启动项后，将看到Manjaro的启动安装界面，先选择好语言，对于时钟，之后可以使用命令进行统一，再选择**Boot**选项，之后就会进入桌面，并且进行像Ubuntu那样的安装界面，首先是选择手动分区，具体的分区有**/，/home，/opt,/boot/efi，/linuxswap**，前三个分区最好连在一起，方便如果磁盘没有分配合理时进行修改，对于/boot/efi,需要几百M的空间即可，但是要将文件类型选择为FAT32,同时标记为Boot,**如果你没有进行这一步，后续会进行警告，留意**，而交换分区8到10g即可，目前我还没有使用过，毕竟系统资源的占用比率没有那么高，后续都是比较相似的安装步骤了。安装结束后，要再次进入Bios界面将Manjaro选项的启动项设为最高优先级，这样每次启动电脑时都可以选择是Manjaro还是windows。

### 5.配置

* 换源

  ``` shell
  sudo pacman-mirrors -i -c China -m rank
  ```

  在筛选出来的选项中选择第一个即可，随后编辑**/etc/pacman.d/mirrorlist**,在China部份添加，刚刚选择的地址（可以在终端复制）

* 更新

  ``` shell
  sudo pacman -Syyu 
  ```

* 导入GPG key,使得archlinuxcn软件源可以正常使用

  ``` shell
  sudo pacman -S archlinuxcn-keyring
  ```

* sudo pacman -S archlinuxcn-keyring加入archlinuxcn源

  编辑**/etc/pacman.conf**,在最底部archlinux中添加国内镜像源（也可以与之前保持一致）

* 安装yay

  ``` shell
  sudo pacman -S yay 
  ```

  这个命令更好管理软件包，且支持更多的包

**到这里，就完成了部份铺垫，但是要作为日常使用的电脑，肯定是远远不够的，后续的软件按需安装，在这其中会遇到很多问题，建议参考：**

https://wiki.archlinux.org/

（ps：打不开？很慢？小猫咪😊）
