# Requirement 要求
## ubuntu电脑系统（须为14.04或16.04的64位ubuntu系统）
    须安装软件：make,gcc,curl,git,autoconf,automake,pkg-config,libtool,libncurses5-dev,autotools-dev,flex,bison,gperf(3.0.4):
    sudo apt-get install make gcc curl
    sudo apt-get install git
    sudo apt-get install autoconf automake pkg-config libtool libncurses5-dev autotools-dev flex bison
    sudo apt-get install gperf=3.0.4-1
   
    同时下载 repo 工具，并确保它在PATH中并可执行：
    mkdir ~/bin
    PATH=~/bin:$PATH
    curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
    chmod a+x ~/bin/repo
## win10自带Ubuntu系统（须为14.04或16.04的64位ubuntu系统）
    与ubuntu电脑有两点不同
    1. 软件源更换为中科大源，即/etc/apt/下的source.list文件的内容替换为以下内容：
        deb https://mirrors.ustc.edu.cn/ubuntu/ bionic main restricted universe multiverse
        deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic main restricted universe multiverse
        deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
        deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
        deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
        deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
        deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
        deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
        deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
        deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
    2. gperf安装不用选定版本，直接执行sudo apt-get install gperf
    
# Download 代码
    repo init -u https://github.com/FishsemiCode/manifest.git -b u1 -m u1.xml
    repo sync
    
# Build 构建
    ./build.sh u1/ap -j4
  
    build生成image out/u1/ap.bin
    prebuilt images: vendor/images cp.bin, sp.bin, ptable.bin
    
# Release 版本

    images/
    ├── ap.bin
    ├── cp.bin
    ├── ptable.bin // 分区表
    └── sp.bin
