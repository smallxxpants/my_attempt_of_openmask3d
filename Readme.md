### 参考仓库
https://github.com/OpenMask3D/openmask3d.git
### 配置环境
1.试着在windows下直接安装，发现只能用于linux

2.在Ubuntu上直接安装，发现需要cuda11.3

cuda安装链接

https://developer.nvidia.com/cuda-11.3.0-download-archive?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=20.04&target_type=runfile_local

3.安装cuda11.3失败，发现是gcc版本过高,cuda11.3要求gcc版本不高于10

4.安装完gcc发现仍然失败，检查是发现Ubuntu没有安装gpu驱动

5.发现是由于ubuntu无法虚拟出显卡，所以应该先安调用物理机的显卡

6.发现虚拟机是不能这样操作的，后来在师兄建议下在服务器直接安装conda跑

### 有用的操作
//采用VMware Ubuntu 24.0 版

1.在虚拟网络编辑器中打开共享文件可以实现虚拟机和物理机互相复制黏贴

2.在虚拟机想共享物理机vpn，参考以下链接

https://blog.csdn.net/nomoremorphine/article/details/138738065

3.切换gcc/g++版本

https://blog.csdn.net/muxuen/article/details/135298656

4.安装GPU驱动教程

