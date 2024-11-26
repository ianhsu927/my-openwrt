# Mac 编译 ImmortalWrt

macOS 下编译 OpenWRT 失败,偶然看到 hanwckf 的 [Mac mini 2024 (Apple M4) openwrt 编译测试](https://cmi.hanwckf.top/p/mac-mini-m4-openwrt-build-test/)启发,使用 [OrbStack](https://orbstack.dev) 搭建虚拟环境，编译成功。

OrbStack 能图形化配置虚拟机和 Docker 环境，非常方便。

ARM64 的 Ubuntu 所需的依赖和 X86_64 的 Ubuntu 有差异.

```bash
# 安装 ARM64 依赖
sudo apt update -y
sudo apt upgrade -y
sudo apt install -y ack antlr3 asciidoc autoconf automake autopoint binutils bison build-essential \\
  bzip2 ccache clang cmake cpio curl device-tree-compiler ecj fastjar flex gawk gettext \\
  git gnutls-dev gperf haveged help2man intltool libelf-dev \\
  libglib2.0-dev libgmp3-dev libltdl-dev libmpc-dev libmpfr-dev libncurses5-dev libncursesw5 \\
  libncursesw5-dev libpython3-dev libreadline-dev libssl-dev libtool lld llvm lrzsz mkisofs msmtp \\
  nano ninja-build p7zip p7zip-full patch pkgconf python2.7 python3 python3-pip python3-ply \\
  python3-pyelftools qemu-utils re2c rsync scons squashfs-tools subversion swig \\
  texinfo uglifyjs upx-ucl unzip vim wget xmlto xxd zlib1g-dev gcc-arm-linux-gnueabihf g++-arm-linux-gnueabihf
```

```bash
# clone immortalwrt 项目中 mt7988 分支
git clone https://github.com/padavanonly/immortalwrt-mt798x.git --branch=mt7988
```

```bash
# feeds.conf.default
./scripts/feeds update -a
./scripts/feeds install -a

make menuconfig
# > .config
make defconfig # 默认配置

make V=s download -j10
make V=s -j10
```

### 一些出错情况

```bash
# mbedtls 失败
make package/libs/mbedtls/clean
```

```bash
# bootstrap-go
sudo apt install golang-go -y
# 把 `CONFIG_GOLANG_EXTERNAL_BOOTSTRAP_ROOT` 改为 `"/usr/bin/go"`
```
