# Requirement 要求
    
    ubuntu环境下安装make, gcc, curl, git tools, autoconf, automake, pkg-config, libtool, libncurses5-dev, autotools-dev, flex, bison, gperf(3.0.4):
    sudo apt-get install make gcc curl
    sudo apt-get install git
    sudo apt-get install autoconf automake pkg-config libtool libncurses5-dev autotools-dev flex bison
    sudo apt-get install gperf=3.0.4-1

   
    同时下载 repo 工具，并确保它在PATH中并可执行：
    mkdir ~/bin
    PATH=~/bin:$PATH
    curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
    chmod a+x ~/bin/repo

# Download 代码
    repo init -u git@github.com:FishsemiCode/manifest.git -b u1 -m u1.xml
    repo sync
    
# Build 构建
    ./build.sh u1/ap -j4
  
    build生成image out/u1/ap.bin
    prebuilt images: vendor/images cp.bin, sp.bin, ptable.bin

    注意：如果要build menuconfig，则要先执行以下命令：
    cd nuttx/tools/kconfig-frontends/
    autoreconf -fi
    ./configure && make
    cd ../../..
    ./build.sh u1/ap menuconfig
    
# Release 版本

    images/
    ├── ap.bin
    ├── cp.bin
    ├── ptable.bin // 分区表
    └── sp.bin
