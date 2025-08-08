## Building Kernel

#### Install Dependencies

```bash
sudo apt update && sudo apt install -y build-essential libncurses-dev bison flex libssl-dev libelf-dev bc
```

#### Download Kernel Source

Download latest lts version from [kernel.org](https://www.kernel.org/).

> longterm: 6.12.41	2025-08-01  [[tarball](https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-6.12.41.tar.xz)]

```bash
export LINUX_KERNEL_VERSION=6.12.41
wget https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-$LINUX_KERNEL_VERSION.tar.xz
tar -xf linux-$LINUX_KERNEL_VERSION.tar.xz
```

#### Configure the Options

```bash
cat ./config.txt > linux-$LINUX_KERNEL_VERSION/.config
```

#### Build Kernel

```bash
cd linux-$LINUX_KERNEL_VERSION/
make -j$(nproc)
```

### Make Modules

```bash
make modules
rm -rf _rootfs && mkdir _rootfs
make INSTALL_MOD_PATH=~/linux/_rootfs modules_install
```
