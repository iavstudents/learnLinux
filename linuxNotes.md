## Symlink

```
ln -s $HOME/.oh-my-zsh           /root/.oh-my-zsh
ln -s $HOME/.zshrc               /root/.zshrc
```

# Arch

### Reflector

```
sudo reflector --verbose --latest 5 --sort rate --save /etc/pacman.d/mirrorlist
```

## Record Screen

```
ffmpeg -f x11grab -s 1366x768 -i :0.0 foryoubro.mkv
```

## Extract mp3 from video

```
ffmpeg -i video.mkv name.mp3
```

## Mount NTFS

```
sudo ntfsfix /dev/sda5
sudo mkdir /media
sudo mount /dev/sda5 /media
sudo umount /media
```
