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

### Pinch to zoom
- https://forum.manjaro.org/t/2-finger-pinch-zoom-gesture-not-working-smoothly-on-kde/99013

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

Last installation:
- https://medium.com/@rajgadhiya011/how-to-setup-flutter-on-arch-linux-with-android-sdk-a-step-by-step-guide-f40450b55669

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

### R
- package ‘RGtk2’ (or other) is not available for this version of R:
  - https://rattle.togaware.com/rattle-install-troubleshooting.html
  - Only use ```install.packages("https://cran.r-project.org/src/contrib/Archive/RGtk2/RGtk2_2.20.31.tar.gz", repos=NULL)``` and replace **https://cran.r-project.org/src/contrib/Archive/RGtk2/RGtk2_2.20.31.tar.gz** with the correct package.

### Installing RStudio
In this page I found the method to install RStudio https://bbs.archlinux.org/viewtopic.php?id=225057:

Code:
```
wget https://aur.archlinux.org/cgit/aur.git/snapshot/rstudio-desktop.tar.gz
tar xfvz rstudio-desktop.tar.gz
cd rstudio-desktop
makepkg -si
```

### Install other packages that aren't in pacman repositories
- Search package in **https://archlinux.pkgs.org/**. Then type:
```
wget "Binary Package url"
```
Example:
```
wget https://aur.andontie.net/x86_64/rstudio-desktop-bin-2021.09.2.382-1-x86_64.pkg.tar.zst
```

### Download tar.gz of packages from ArchLinux
- In **package options** select **Download snapshot**.


### Remove cache of old applications from wine
```
rm -f ~/.config/menus/applications-merged/wine*
rm -rf ~/.local/share/applications/wine
rm -f ~/.local/share/desktop-directories/wine*
rm -f ~/.local/share/icons/????_*.{xpm,png}
rm -f ~/.local/share/icons/*-x-wine-*.{xpm,png} }}}
```

### Search text inside of files
- https://fortinux.gitbooks.io/humble_tips/content/usando_la_linea_de_comandos/tutorial_usar_grep_para_buscar_texto_dentro_de_archivos_en_gnulinux.html
- https://ed.team/blog/como-buscar-dentro-de-archivos-en-linux
```
grep -rni "palabra" .
```

### Change words in multiple files
En el siguiente ejemplo, usaremos sed para reemplazar todas las ocurrencias de la palabra «mongo» por la palabra «aurelio» en todos los archivos que tengan la extensión .txt y que se encuentren en la carpeta /home/usuario/micarpeta/.
```
find /home/usuario/micarpeta/ -name '*.txt' -exec sed -i "s/mongo/aurelio/g" {} \;
```
Me di cuenta que es mejor poner el **.txt** entre comillas, sino **find** saca errores raros.

Ref: https://blog.desdelinux.net/como-encontrar-y-reemplazar-texto-en-varios-archivos-desde-el-terminal/


### ranger colorscheme of editor text
I changed to use vim for noevim with this:
https://unix.stackexchange.com/questions/367452/how-to-change-the-default-text-editor-in-ranger

### Solving problems with Matlab and Simulink
https://la.mathworks.com/matlabcentral/answers/364551-why-is-matlab-unable-to-run-the-matlabwindow-application-on-linux


### Error writing the file failed to close the package enlace cruzado entre dispositivos no permitido **simulink**
https://bbs.archlinux.org/viewtopic.php?id=277970

### Removing sensitive data from GitHub
https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository

### ssh: connect to host github.com port 22: Connection timed out' error
https://gist.github.com/Tamal/1cc77f88ef3e900aeae65f0e5e504794

### Problem with some programs after updating Python (ranger, etc)
- https://www.reddit.com/r/archlinux/comments/rfj0av/global_problem_with_python_310/
- https://www.reddit.com/r/archlinux/comments/rf6c84/psa_python_310_is_in_core_rebuild_your_aur/

### Problem with Kernel in Jupyter notebook
- https://stackoverflow.com/questions/65300509/jupyter-notebook-python-kernel-filenotfounderror-errno-2-no-such-file-or-di

### Problem in Chrome and some other applications when entering in full screen mode (xmonad)
- https://www.reddit.com/r/xmonad/comments/wb9ot6/entering_fullscreen_in_chromium_cuts_off_some_of/

### Problem when dialog (popup) window open over another dialog window. The last one spawn behind the first
- https://www.reddit.com/r/xmonad/comments/hncn6v/raise_popup_windows_created_by_floating_windows/

## Zsh
I used the following command to map **Shift+Tab** with autocompletion in zsh:
```
bindkey '^[[Z' autosuggest-accept
```
- https://stackoverflow.com/questions/71344843/how-do-i-remap-the-tab-key-in-zsh-autosuggestion-to-replace-the-%E2%86%92

## NeoVim
### Codeium in Neovim
There wasn't integration of Codeium with Coc, so I used Plug
- https://github.com/Exafunction/codeium.vim

### Jupyter Notebooks in Nvim
I use vim-jukit:
- https://www.reddit.com/r/neovim/comments/wzoa8i/jupyter_notebooks_in_neovim_any_good_way/

### yay is broken after update
- https://github.com/Jguer/yay/issues/2393

### Change HDMI and screens automatically
- https://github.com/phillipberndt/autorandr

### Failed to load python3 host
- https://github.com/fsharp/zarchive-vim-fsharp/issues/96

Then, I installed the last thing with the following command:
- [sudo pacman -S python-lsp-server](https://github.com/atom-community/ide-python/issues/116)
```
sudo pacman -S python-lsp-server
```

### Anaconda y miniconda
Here I found how to install miniconda:
- https://docs.anaconda.com/miniconda/miniconda-install/

And here a good way to manage Anaconda in Arch:
- https://www.reddit.com/r/archlinux/comments/w3pk9n/comment/igy182u/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button

If I want to remove Anaconda, I can read the following discussion:
- https://stackoverflow.com/questions/29596350/how-to-uninstall-mini-conda-python

I had ```Conda command not found```, so I ran the command ```conda init```

And finally, as I don't want to activate the base environment by default, here is how can I achieve this:
- https://stackoverflow.com/questions/54429210/how-do-i-prevent-conda-from-activating-the-base-environment-by-default


