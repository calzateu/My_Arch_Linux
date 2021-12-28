# My_Arch_Linux

### Scrolling
- https://www.reddit.com/r/archlinux/comments/b64k4s/reverse_scrolling/
- https://wiki.archlinux.org/title/Libinput#Via_Xorg_configuration_file

```
Section "InputClass"
        Identifier "mytouchpad"
        Driver "libinput"
        MatchIsTouchpad "on"
        Option "NaturalScrolling" "true"
EndSection
```

### Wifi
- https://bbs.archlinux.org/viewtopic.php?id=244415
- https://wiki.archlinux.org/title/Network_configuration/Wireless#iwlwifi

```
sudo vim /etc/modprobe.d/iwlwifi.conf
```
Then add:
```
options iwlwifi 11n_disable=1 swcrypto=1
```

### Vim
- https://linuxhint.com/vim_syntax_highlighting/

Then see following file to know the categories:
```
vim /usr/share/vim/vim82/colors/tools/check_colors.vim
```
And add this code to **/usr/share/vim/vim82/colors/elflord.vim**
```
hi ColorColumn ctermbg=lightgreen guibg=lightgreen
```
