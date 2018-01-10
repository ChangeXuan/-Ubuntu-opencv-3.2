# UbuntuConfigureOpencv-3.2
## 在网上可以找许多方法，也大多正确，在这里主要记录了我自己成功配置opencv3.2的过程
- 更新apt-get 
```
$ sudo apt-get update
$ sudo apt-get upgrade
```
- 安装依赖
```
$ sudo apt install libjpeg8-dev libtiff5-dev libjasper-dev libpng12-dev libgtk2.0-dev libavcodec-dev libavformat-dev libswscale-dev libv4l-dev libatlas-base-dev gfortran libhdf5-serial-dev libeigen3-dev python2.7-dev ffmpeg libopencv-dev libgtk-3-dev libdc1394-22 libdc1394-22-dev libjpeg-dev libxine2-dev libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libtbb-dev qtbase5-dev libfaac-dev libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev libtheora-dev libvorbis-dev libxvidcore-dev x264 v4l-utils unzip
```
- 下载源码(也可以手动下载)
```
$ weget https://github.com/Itseez/opencv/archive/3.2.0.zip unzip 3.2.0.zip
```
- 编译源码
```
$ cd opencv-3.2.0
$ mkdir build
$ cd build
$ cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D WITH_TBB=ON -D BUILD_NEW_PYTHON_SUPPORT=ON -D WITH_V4L=ON -D WITH_QT=ON -D WITH_OPENGL=ON ..
### (若cmake过程中ippicv_linux_20151201.tgz这个文件一直无法下载(下载地址见底部)，则可手动下载，并放到‘/home/xxx/opencv-3.2.0/3rdparty/ippicv/downloads/linux-808b791a6eac9ed78d32a7666804320e’中)
### (若在cmake过程中报错说找不到Qt×，则需要把3.2.0.zip重新解压并覆盖当前的opencv-3.2.0,然后再执行
$ cd opencv-3.2.0
$ mkdir build
$ cd build
$ cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D WITH_TBB=ON -D BUILD_NEW_PYTHON_SUPPORT=ON -D WITH_V4L=ON -D -D WITH_OPENGL=ON ..$ )
```
- 安装
```
$ sudo make
$ sudo make install
```
- 整理
```
$ sudo apt-get update
```
- 测试
```
$ python
>>> import cv2
>>> cv2.__version__
'3.2.0'
>>>
```
##下载 [ippicv_linux_20151201.tgz](https://pan.baidu.com/s/1c4lOnLm) (密码：ej2i)
