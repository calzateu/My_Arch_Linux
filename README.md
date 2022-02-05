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
        Option "Tapping" "on"
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
And add this code to **/usr/share/vim/vim82/colors/elflord.vim**. It for the color of column
```
hi ColorColumn ctermbg=lightgreen guibg=lightgreen
```

Then, add this code to **/usr/share/vim/vim82/colors/elflord.vim**. It for unnecessary white spaces
```
...
hi WhiteSpaces ctermbg=red guibg=red
...
hi link ExtraWhitespace WhiteSpaces

```

### Pacman
https://stackoverflow.com/questions/27681785/fixing-target-not-found-in-pacman-maybe-mirrorlist-of-pacman-conf

### MySQL
Second solution:
- https://www.databasestar.com/access-denied-for-user-root-at-localhost/

### Specify Java version
- https://rtfm.co.ua/en/arch-linux-set-a-java-version/

### Solved GRUB problem
Make a directory in /boot called ***efi***.
```
mkdir /boot/efi
```
Mount EFI disk to /boot/efi
```
mount /dev/nvme0n1p1 /boot/efi
```
Then configure grub
```
grub-install --target=x86_64-efi --efi-directory=/boot/efi/ --bootloader-id=GRUB
grub-mkconfig -o /boot/grub/grub.cfg
```
Now everything is ready with grub. Umount live USB and restart :D

Sources:
- https://www.youtube.com/watch?v=ZmTB4YlNZds
- https://bbs.archlinux.org/viewtopic.php?pid=1962038#p1962038

### Flutter
I have *google-chrome-stable*, so I did the following
```
sudo cp /usr/bin/google-chrome-stable /usr/bin/google-chrome
```
Source:
- https://stackoverflow.com/questions/66631883/cannot-find-chrome-try-setting-chrome-executable-to-a-chrome-executable-flutte

### Dart SDK
It usually happens with projects that were created in other machines. To fix this on Android Studio 3.1.3:

1. File-> Settings (ctrl+alt+s)
2. Languages and Frameworks -> Dart
3. Check "Enable Dart support for the project..."
4. In "Dart SDK path" click in "..." and navigate to flutter SDK directory. Under that directory you'll find "bin/cache/dart-sdk". This is the dart sdk path you should use.
5. Click "Apply"
6. Close the project and open it again (sometimes you need this step, sometimes doesn't)

Source:
- https://stackoverflow.com/questions/48650831/dart-sdk-is-not-configured

### WoeUSB not formating the USB disk
Remove **udiskie -t &** from **~.xprofile**

### Change BASH Shell Color of Shell Prompt
- https://www.cyberciti.biz/faq/bash-shell-change-the-color-of-my-shell-prompt-under-linux-or-unix/
- https://unix.stackexchange.com/questions/148/colorizing-your-terminal-and-shell-environment

### Alacritty problem
- https://stackoverflow.com/questions/24676687/top-xterm-unknown-terminal-type/28290724
