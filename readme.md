# grub multiboot usb

Boot multiple operating systems with grub from usb flash drive

## Description

Describes how to create a grub multiboot usb flash disk, boots linux and windows

## Dependencies

ubuntu

## Usage

Format a 16GB usb flash disk and create the required partitions on it

Use gparted to format and partition the flash disk

``` 
partition type gpt

Assuming your usb drive is sdb

Partitions
sdb1 - fat32 - 512MB
sdb2 - ntfs - 6GB
sdb3 - ext4 - 7GB or whatever space is left

```

Install grub on sdb1, assuming your usb device is sdb

```
mount /dev/sdb1 /mnt

grub-install --force --removable --target=x86_64-efi --boot-directory=/mnt/boot --efi-directory=/mnt /dev/sdb

```

Copy windows iso contents to sdb2

Create a folder called iso on sdb3
Copy ubuntu and fedora iso's to this folder, make sure their filenames match what is defined in grub.cfg

Copy grub.cfg to sdb1 /boot/grub folder

For memtest, download (from https://www.memtest.org/) and copy the memtest file from the memtest iso to sdb1/

Boot your usb flash disk to test!
