# Arch Linux Installation

hi, this is my personal guide of arch linux installation

i write this based on my trial error, damn arch when update kernel make entire system broken!!!

my machine is

Acer V5-57G with dual vga and efi mode

I mean, hope you not follow all if it was not same as your machine

but biggest steps are same

make configuration as your preferences

my config

- Arch Linux
- BSPWM window manager
- Polybar statusbar
- ST terminal

you can download my dotfiles from my github account

[alfianguide dotfiles](http://github.com/alfianguide/dotFiles)

## Guide

```
thing like this is executing a command, ok!
```

## Before

download iso image form archlinux.org/download

burn iso image you download with dd command

## Ingredients

- Laptop
- Arch Linux Bootable ISO
- Internet
- Brain

## First Thing First

## Check your internet connection

I prefer wired connection, but wifi is ok though

### Wired

just plug in your wired connection

### Wifi

```
wifi-menu
```

select your wifi, and enter the password and you connected!

if all done, check your connection with

```
ping archlinux.org
```

if there's data reply, congrats you are connected to the internet!!!

## Prepare Partition

check your partition with

```
fdisk -l
```

then part it one by one, with

```
cfdisk
```

partition reccomendation is

- boot
- system
- home user
- swap

with each size as your preferences

if done, then format it to linux filesystem, but let's see again first,

```
fdisk -l
```

format, for example /dev/sda1 for the boot

```
mkfs.fat -F32 /dev/sda1
```

format the system and home

```
mkfs.ext4 /dev/sda2
mkfs.ext4 /dev/sda3
```

make swap

```
mkswap /dev/sda4
swapon /dev/sda4
```

/dev/sda above is an example for each partition, don't follow it, look at your fdisk!!!


## Mount Partition

mount partition of system and home first.

mount system

```
mount /dev/sda1 /mnt
```

mount home

```
mkdir /mnt/home
mount /dev/sda1 /mnt/home
```

## Install Arch

this is my favourite step, install arch!

```
pacstrap /mnt base base-devel
```


## Make automount

make automount of the mounted system, home, and swap

```
genfstab -U -p /mnt >> /mnt/etc/fstab
```

## Change Root

change root into installed arch linux that has done before

```
arch-chroot /mnt
```

## Install Editing Apps

```
sudo pacman -S neovim
```

i like editing with vim... i mean... neovim

## System Clock & Timezone

update system clock

```
timedatectl set-ntp true
```

select timezone

```
ln -sf /usr/share/zoneinfo/Asia/Jakarta /etc/localtime
```

clock synchronize to UTC

```
hwclock --systohc
```

## Localization

```
nvim /etc/locale.gen
```

uncomment en_US.UTF-8 UTF-8

```
locale > /etc/locale.conf
```

## Network Config

```
nvim /etc/hostname
```

enter your PC name, such as Alfian-PC

```
nvim /etc/hosts
```

add

127.0.0.1 localhost
::1       localhost
127.0.0.1 Alfian-PC.localdomain Alfian-PC

## Set Root Password

```
passwd
```

## Install Bootloader

I'm using GRUB bootloader

```
pacman -S grub efibootmgr
```

make dir for grub efi to be mounted

```
mkdir /boot/efi
```

```
mount /dev/sda1 /boot/efi
```

install grub

```
grub-install --target=x86_64.efi --bootloader-id=GRUB --directory=/boot/efi
```

grub config

```
grub-mkconfig -o /boot/grub/grub.cfg
```

basically this is the end of minimal install Arch Linux, but don't go anyway, our system isn't completed yet!

hei this is my personal guide, if you want to follow along, please, have a sit, but if not, it's ok

## Make User

```
useradd -m -g users -G wheel alfianguide
```

-m is to makedir, it's optional when you reinstall arch linux, don't add it.

```
passwd alfianguide
```

set password and then change to it

```
su - alfianguide
```

## Install Yay

yay is my favourite package manager beside pacman, yay is based on go, so go will be downloaded first

```
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

just use 'yay'

to update entire system

## Install Graphical Things 

here, we install such a thing, X server, file manager, browser, etc.

start by X server and it's friends

```
pacman -S xorg-server xorg-xinit xorg-xprop xorg-xsetroot
```

then install windows manager

```
yay -S bspwm sxhkd
```

then the statusbar

```
yay -S polybar
```

and create .xinitrc in $HOME or /home/user directory

add 'exec bspwm' to it

app launcher

```
yay -S rofi
```

## Install Networking Things

I use connman as my network manager

```
yay -S wpa_supplicant connman connman-gtk
```

enable wifi support

```
connmanctl enable wifi
```

enable connman service

```
systemctl enable connman
```

## Install Fonts

Code New Roman

```
yay -S otf-code-new-roman
```

FontAwesome

```
yay -S awesome-terminal-fonts
```

## Install Basic Apps

wget magic

```
yay -S wget
```

terminal

```
wget https://dl.suckless.org/st/st-0.8.2.tar.gz
```

```
tar -xvf st-0.8.2.tar.gz
```

```
cd st-0.8.2
```

```
make clean install
```

file manager

use ranger for minimalist

```
pacman -S ranger highlight poppler ffmpegthumbnailer mediainfo w3m
```

install browser

```
pacman -S firefox
```

## Install Multimedia

install audio driver, damn alsa not work on my machine

```
pacman -S pulseaudio
```

I use mpv as multimedia player

```
yay -S mpv
```

I use spotify as my music player

```
yay -S spotify
```

don't forget feh to set background image

```
yay -S feh
```

sxiv image viewer

```
yay -S sxiv
```

screenshot with scrot

```
yay -S scrot
```

youtube-dl maybe? for downloading youtube and as streaming youtube dependency for mpv

```
yay -S youtube-dl
```

## Patch and Fixes

Download my dotfiles

```
git clone http://github.com/alfianguide/alfianguide-dotfiles.git
```

and copy all of it to $HOME

## All Font Same

```
cd /etc/fonts/conf.d
```

and set 45-latin.conf to Code New Roman by adding 

<alias>
	<family>Code New Roman</family>
	<default><family>serif</family></default>
</alias>

to first line of serif, sans-serif, monospace

and then edit the 60-latin.conf by adding

<family>Code New Roman</family>

to first line of prefer in serif, sans-serif, monospace

OVERKILL EH? WHATEVER!!!!!

## Fix Touchpad Tap

Tap to click

```
sudo mkdir -p /etc/X11/xorg.conf.d
sudo nvim /etc/X11/xorg.conf.d/90-touchpad.conf
```

add these inside it

```
Section "InputClass"
        Identifier "touchpad"
        MatchIsTouchpad "on"
        Driver "libinput"
        Option "Tapping" "on"
        Option "TappingButtonMap" "lrm"
        Option "NaturalScrolling" "on"
        Option "ScrollMethod" "twofinger"
EndSection
```

what's next?

reboot

```
umount -R /mnt
```

```
reboot
```


### Notes

The main point on arch linux installation is
- it's base installed on drive and automount by fstab
- root password set
- connection driver and tools like connman or networkmanager, but i prefer connman with connman-gtk as gui
- xorg and minimal wm, like bspwm or i3
- bootloader, to get away the disk installation

the important things is FAST INTERNET CONNECTION!

any additional things like multimedia, fonts, tools can be installed later after the system is boot fine with very minimalist system and without disk installation boot of course.
