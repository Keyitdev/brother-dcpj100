
# Brother DCP-J100

## Driver for the Brother DCP-J100 multifuncional printer made by Keyitdev in 2023.

Build package.
```
makepkg -si
```

Enable multilib in the pacman config by uncommenting these two lines in pacman.conf: 

```
vim /etc/pacman.conf
```

```
[multilib]
Include = /etc/pacman.d/mirrorlist
```

```
pacman -Syu
```

Add user to lp group using gpasswd.

```
gpasswd -a <USER> lp
```

Enable cups.
```
systemctl enable cups.service
systemctl start cups.service
```
> https://localhost:631


## Scanner 

If you want to use dcpj100 scaner install 'simple-scan' 'brscan4' packages.

```
yay -S simple-scan brscan4
```
