# freefilesync

# 编译freefilesync的Arm64版本
官方下载：https://freefilesync.org/download.php
官方提供：Windows、Linux(x86_X64)、MacOS版本 以及源码下载

## 使用PPA上的源码进行编译
直接编译源码会报错，建议下载https://launchpad.net/ 上的源码然后编译
在launchpad中搜索freefilesync，很遗憾没有找到Arm64版本，不过有位大佬在更新Linux的x86_x64版本。
主页：https://launchpad.net/~xtradeb/+archive/ubuntu/apps
下载源码：https://ppa.launchpadcontent.net/xtradeb/apps/ubuntu/pool/main/f/freefilesync/
在目录中存在 `.debian.tar.xz` `.dsc` `.orig.tar.xz` `.deb` 文件 我们要编译Arm架构的，这里先看最新12.3版本的dsc文件 要求libcurl4-openssl-dev (>= 7.84) 当前系统环境不满足，我是小白不懂这个，这里我们选择11.25版本，我的ubuntu22.04编译了gcc13，其他也满足依赖要求。
下载以下3个文件：
```
freefilesync_11.25-1~xtradeb1.debian.tar.xz
freefilesync_11.25-1~xtradeb1.dsc
freefilesync_11.25.orig.tar.xz                 # 源码
```
新建一个文件夹 freefilesync_build 将这3个文件放进去
```
cd freefilesync_build
tar xf freefilesync_11.25-1~xtradeb1.debian.tar.xz   # 解压 后有一个debian的目录
tar xf freefilesync_11.25.orig.tar.xz                # 解压 源码
dpkg-buildpackage -uc -b # 执行编译，如果没有权限请加sudo，编译过程较长，注意散热。
sudo dpkg -i freefilesync_11.25-1~xtradeb1_arm64.deb # 找到deb包后安装
```
当前系统使用的是g++，编译时源码里是g++-12，可以将源码中所有的g++-12修改为g++，使用ide修改很方便，或者创建软连接，命名为g++-12（这里没有使用这种）。
编译并安装完成后，启动后
点击Tools-Language-简体中文 修改中文
重新启动 点击帮助-关于，这里显示 `版本：11.25 x86-64 for Ubuntu 2022年09月04日` 不要介意。
