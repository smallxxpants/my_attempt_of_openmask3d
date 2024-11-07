### 参考仓库
https://github.com/OpenMask3D/openmask3d.git
### 配置环境
在服务器中安装

参考链接：https://zhuanlan.zhihu.com/p/440548295 

1.可以直接把sh文件从windows中直接拉到远程服务器的文件下

2.注意安装anaconda不要安装到home下，而是安装到data下

3.git相关命令执行不了，服务器的问题，只能从github下载源码上传上去：

例：从github上下载了detectron2后上传至服务器并安装：先用git命令下载到本地，然后在上传文件夹，之后用cd detectron2 && pip install -e .命令安装

4.遇到cuda版本不匹配的问题，应该多安装一个cuda11.3版本

教程：https://blog.csdn.net/qq_41917697/article/details/114437924

#export PATH=/usr/local/cuda-9.0/bin${PATH:+:${PATH}}  

#export LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}

#export CUDA_HOME=/usr/local/cuda-9.0/

#export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-9.0/extras/CUPTI/lib64

5.安装MinkowsKiEngine的时候总是不成功，报错如下

![image](https://github.com/user-attachments/assets/10b3ff03-db37-4a4d-99a9-e9f1e47d9933)

解决方法：采用

python setup.py install --blas_include_dirs=${CONDA_PREFIX}/include --blas=openblas 

这个命令而不是简单的pip install -e. 当然还做了一个setuptool降版本到50.0的操作

参考教程：https://blog.csdn.net/m0_60197472/article/details/125293739

### 正式训练

1.

--------------------------------------------------------------------------------
### 新名词学习
.ckt 文件：检查点（checkpoint）文件，作用是记录模型在特定时间点的参数值，一般为模型权重、优化器状态等信息，以便于之后的模型恢复、评估或继续训练。

.pth文件： 常用于 PyTorch 框架，用于存储模型的状态信息（例如各层的参数和权重）。该文件可以直接加载到 PyTorch 中，用于模型的恢复、评估或迁移学习。

### 失败的操作
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

