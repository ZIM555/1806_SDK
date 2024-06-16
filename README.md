# Clean OpenWRT 18.06 for Gl-Inet SFT1200 (Opal)

How to build

apt-get install ack antlr3 asciidoc autoconf automake \
autopoint binutils bison build-essential bzip2 ccache \
clang cmake cpio curl device-tree-compiler fastjar flex \
gawk gettext gcc-multilib g++-multilib git gperf haveged \
help2man intltool libc6-dev-i386 libelf-dev libglib2.0-dev \
libgmp3-dev libltdl-dev libmpc-dev libmpfr-dev libncurses5-dev \
libncursesw5-dev libreadline-dev libssl-dev libtool lrzsz mkisofs \
msmtp nano ninja-build p7zip p7zip-full patch pkgconf python2.7 python3 \
python3-pyelftools libpython3-dev qemu-utils rsync scons squashfs-tools \
subversion swig texinfo uglifyjs upx-ucl unzip vim wget xmlto xxd \
zlib1g-dev libfuse-dev

git clone https://github.com/ZIM555/SFT1200-1806_SDK.git

cd SFT1200-1806_SDK

git config --global user.email "you@email.com"

git config --global user.name "Developer"

git reset --hard

git clean -df

git apply patches-siflower-18.x/*.patch

cd openwrt-18.06

./scripts/feeds update -a

./scripts/feeds install -a

make menuconfig

export FORCE_UNSAFE_CONFIGURE=1

wget https://github.com/wekingchen/Actions-SFT1200/raw/main/board-2.bin.ddcec9efd245da9365c474f513a855a55f3ac7fe -P dl/

make -j$(nproc) V=s
