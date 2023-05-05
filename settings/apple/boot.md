# 引导

* [操作系统](boot.md#cao-zuo-xi-tong)
* [Bootloader](boot.md#bootloader)
* [Linux 设置](boot.md#linux-she-zhi)
  * [Kernel 镜像](boot.md#kernel-jing-xiang)
  * [Ramdisk](boot.md#ramdisk)
  * [引导参数](boot.md#yin-dao-can-shu)
* [**(macOS 12+)** macOS 设置](boot.md#macos-12+-macos-she-zhi)
  * [IPSW Install Image](boot.md#ipsw-install-image)

## 操作系统

目前只有 **(macOS 12+)** 支持 macOS 和 Linux。

## Bootloader

与使用默认 Bootloader 的操作系统（macOS/Linux）相同。**(macOS 13+)** 引导具有图形支持的 Linux 必须使用 UEFI Bootloader。

## Linux 设置

### Kernel 镜像

选择一个要被引导的**未压缩的** Linux Kernel。

### Ramdisk

（可选）选择一个预启动内存盘 (initial ramdisk)。

### 引导参数

内核引导参数。强烈建议添加 `console=hvc0 root=/dev/vda`。

## (macOS 12+) macOS 设置

### IPSW Install Image

导入通用 macOS IPSW 进行安装。
