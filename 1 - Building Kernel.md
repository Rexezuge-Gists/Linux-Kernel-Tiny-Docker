## Building Kernel

#### Install Dependencies

```bash
sudo apt update && sudo apt install -y build-essential libncurses-dev bison flex libssl-dev libelf-dev bc
```

#### Download Kernel Source

Download latest lts version from [kernel.org](https://www.kernel.org/).

> longterm: 6.12.41	2025-08-01  [[tarball](https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-6.12.41.tar.xz)]

```bash
wget -O linux.tar.xz https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-6.12.41.tar.xz
tar -xf linux.tar.xz
```

#### Configure the Options

```bash
cp ./config.txt linux/
```

#### Build Kernel

```bash
cd linux/
make -j$(nproc)
```

### Make Modules

```bash
make modules
rm -rf _rootfs && mkdir _rootfs
make INSTALL_MOD_PATH=~/linux/_rootfs modules_install
```
