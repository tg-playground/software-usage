# Arch Linux Installation Note

Content

- Pre-installation
- Installation
- Configure the system
- Reboot
- Post-installation

## Update time

```
Current Release: 2020.12.01
Included Kernel: 5.9.11
ISO Size: 682.3 MB
```

## Pre-installation

### Get Unallocated Space from Volumn of Windows

Disk Management --> select a disk --> shrink volumn --> Enter the amount of space to shrink in MB: 200000 (200 GB)

### Acquire an installation image

[Download Page](https://archlinux.org/download/)

### Verify signature and md5 checksums

TODO

### *Prepare an installation medium

**Note:** Arch Linux installation images do not support Secure Boot. You will need to [disable Secure Boot](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface/Secure_Boot#Disabling_Secure_Boot) to boot the installation medium. If desired, [Secure Boot](https://wiki.archlinux.org/index.php/Secure_Boot) can be set up after completing the installation.

You need check your computer is enable secure boot in bios. If it's enable must disable it for installing Arch Linux.

### Set the keyboard layout

TODO

### Verify the boot mode

```
ls /sys/firmware/efi/efivars
```

### Connect to the internet

```
ip link
iwctl
device list
station <device> scan
station <device> get-networks
station <device> connect SSID
exit
ping archlinux.org
```

### Update the system clock

```
timedatectl set-ntp true
timedatectl status
```

### *Partition the disks

```shell
# identify devices
lsblk

# create partitions of Linux
cfdisk /dev/<your_disk_device_name_eg_nvme0n1>

1)select Free space -> New -> Enter
# 5 partition
# GPT partition: 512 MB
# root partition: 20 GB
# swap partition: 16 GB
# home partition: rest of the free space
2)Write -> yes -> Quit

# identify devices again
lsblk
```

[Partitioning](https://wiki.archlinux.org/index.php/Partitioning)

[Dual boot with Windows](https://wiki.archlinux.org/index.php/Dual_boot_with_Windows)



```bash
# 检查硬盘
# 这里没有看到之前划分好的空间，不要慌，那是因为之前只是划了空间，并没有建立分区
lsblk

# 建立分区
cfdisk /dev/<nvme0n1>

lsblk

# 分区格式化
mkfs.ext4 /dev/nvme0n1p5

# 挂载分区
mount /dev/nvme0n1p5 /mnt
mkdir /mnt/boot
mount /dev/nvme0n1p2 /mnt/boot

```



### Format the partitions

```
# to create an Ext4 file system on /dev/root_partition
mkfs.ext4 /dev/<root_partition>
# initialize swap
mkswap /dev/<swap_partition>
```



### Mount the file systems

```
# Mount the root volume to /mnt
mount /dev/root_partition /mnt
# enable swap space volume
swapon /dev/swap_partition
```



## Installation

### Select the mirrors

```
reflector --help
reflector -c China -a 6 --sort rate --save /etc/pacman.d/mirrorlist
```



### Install essential packages	

```
pacstrap /mnt base linux linux-firmware
```

```
pacman -S vi vim nano
```



## Configure the system

### Fstab

```
genfstab -U /mnt >> /mnt/etc/fstab
cat /mnt/etc/fstab
```



### Chroot

```
arch-chroot /mnt
```



### Time zone

```
timedatectl status
timedatectl list-timezones
timedatectl set-timezone <Zone>/<SubZone>
timedatectl set-timezone Asia/Shanghai
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
# show datetime
date
```

```
# Set the Hardware Clock from the System Clock, and update the timestamps in /etc/adjtime.
hwclock --systohc
```



### Localization

Edit /etc/locale.gen and **uncomment en_US.UTF-8 UTF-8** and other needed locales. Generate the locales by running:

```
# locale-gen
```

Create the locale.conf(5) file, and set the LANG variable accordingly:

```
/etc/locale.conf
LANG=en_US.UTF-8
```

If you set the keyboard layout, make the changes persistent in vconsole.conf(5):

```
/etc/vconsole.conf
KEYMAP=de-latin1
```



### Network configuration

Create the [hostname](https://wiki.archlinux.org/index.php/Hostname) file:

```
/etc/hostname
myhostname
```

Add matching entries to [hosts(5)](https://jlk.fjfi.cvut.cz/arch/manpages/man/hosts.5):

```
/etc/hosts
127.0.0.1	localhost
::1		localhost
127.0.1.1	myhostname.localdomain	myhostname
```

If the system has a permanent IP address, it should be used instead of `127.0.1.1`.

```
# install the network manager
pacman -S networkmanager
# enable it 
systemctl enable networkmanager
```



### Initramfs

```
mkinitcpio -P
```



### Root password

```
passwd
```



### Boot loader

Install 

```
pacman -S grub efibootmgr
```

#### Install Basic Package

```
pacman -S networkmanager network-manager-applet dialog wireless_tools wpa_supplicant os-prober mtools dosfstools ntfs-3g base-devel linux-headers reflector git sudo
```

Boot 

```
grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=Arch
```

```
mkdir /mnt/windows10
mount /dev/nvme0n1p4 /mnt/windows10
grub-mkconfig -o /boot/grub/grub.cfg
```



这里利用Windows的EFI分区，检查EFI分区号

```
lsblk
```

建立boot文件夹

```text
mkdir /mnt/boot
```

挂载EFI分区

```text
mount /dev/nvme0n1p2 /mnt/boot
```



-

install and mount

```
pacman -S grub efibootmgr
mkdir /boot/efi
mount /dev/<boot_partition_name> /boot/efi
```



## Reboot

```
exit
umount -R /mnt
reboot
```





## Post-installation





