---
layout: post
title: "install archlinux"
date: 2017-01-28 23:49:11 +0000
---

    cfdisk /dev/sda
    mkfs.ext4 /dev/sda1
    mkswap /dev/sda2
    swapon /dev/sda2
    
    mount /dev/sda1 /mnt
    mkdir /mnt/boot
    mount /dev/sda2 /mnt/boot

    pacstrap /mnt base base-devel net-tools
    
    genfstab -U /mnt >> /mnt/etc/fstab
    arch-chroot /mnt
    ln -s /usr/share/zoneinfo/R/C /etc/localtime
    hwclock --systohc
    vim /etc/locale.gen
    locale-gen
    vim /etc/locale.conf

    vim /etc/hostname
    youhostname

    mkinitcpio -p linux
    passwd
    
    pacman -S grub
    grup-install --target=i386-pc /dev/sdx
    grup-mkconfig -o /boot/grub/grub.cfg

    exit
    umount -R /mnt
    reboot
