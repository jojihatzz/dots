</br></br>

# Install Arch ($ archinstall)

</br></br>

![](https://raw.githubusercontent.com/jojihatzz/dots/main/preview.jpg)

---
## Verify Connectivity to the Internet

First of all, check the internet connection. To check internet connectivity, ping a website, as shown in the example below.

```bash
ping -c 3 archlinux.org
```


If you use a wired connection, it is usually picked up automatically. However, if you receive an error message, please check your internet connection or router.

---
## Install using archinstall

Once the boot is complete, you should see a prompt like the below. Type `archinstall` and hit enter.

![First prompt for archinstall](https://www.debugpoint.com/wp-content/uploads/2022/01/image.png)


choose your options and once you are done type exit & reboot.

</br></br>

---
## Post install

1. Install DE
2. Install Apps
3. Customize desktop
4. Configure apps

</br></br>

---
### Install DE

- KDE
- Gnome
- Xfce
- etc

Personally i like KDE

```bash
sudo pacman -S plasma-desktop kdeconnect plasma-pa kscreen
```

</br></br>

---
### Install Packages (pacman)

- htop
- git
- unzip
- firefox
- mlocate
- neofetch
- xorg-server & xorg-xinit
- nvidia & nvidia-settings
- ark
- kcalc
- starship
- dolphin
- celluloid
- discord
- inkscape
- Fsearch
- neovim
- keepass

</br></br>

---
### Install Packages (yay)

Install yay

```bash
git clone https://aur.archlinux.org/yay.git
cd /yay
makepkg -si
```

yay packages
- spotify
- stacer
- visual-studio-code-bin
- stremio-beta
- neo-matrix
- fsearch
- nvim-packer-git
- github-desktop-bin
- ly

</br></br>


> [!info] .Appimage
> If you install .AppImage app extract it with `./Appname --appimage-extract` a directory will be created called `squashfs-root` in the directory where the AppImage was extracted. Enter the directory `squashfs-root` and copy the desktop launcher to /usr/share/applications/ then edit the desktop launcher to point to the path of the AppImage, i.e., `Exec=$HOME/.local/bin/inkscape.AppImage`. Remove the directory `squashfs-root`.move them to home/.local/bin and make a .desktop file.

</br></br>

---
## Configure xinitrc & ly

![](https://user-images.githubusercontent.com/5473047/88958888-65efbf80-d2a1-11ea-8ae5-3f263bce9cce.png)


The xinit program is used to start the [X Window System](https://wiki.debian.org/XWindowSystem) server and a first client program on systems that cannot start X directly from /etc/init or in environments that use multiple window systems. When this first client exits, xinit will kill the X server and then terminate.

If no specific client program is given on the command line, xinit will look for a hidden file in the user's [home_directory](https://wiki.debian.org/home_directory) called .xinitrc to run as a shell script to start up client programs

To make a .xinitrc file from the command line type

```bash
touch .xinitrc
nvim .xinitrc
```

then add your Desktop Environment name

```bash
# exec enlightenment_start
# exec i3
# exec mate-session
# exec xmonad
# exec startlxqt
# exec startlxde
# exec awesome
# exec bspwm
# exec gnome-session
# exec gnome-session --session=gnome-classic
# exec startplasma-x11
# exec startplasma-wayland
# exec startxfce4
# exec startfluxbox
# exec openbox-session
# exec cinnamon-session
# exec pekwm
# exec catwm
# exec dwm
# exec startede
# exec icewm-session
# exec jwm
# exec monsterwm
# exec notion
# exec startdde       # deepin-session
```

**Remove the `#` symbol at the beginning of the code line belonging to your Desktop Environment** (beginning with `# exec`) and save the `~/.xinitrc` file.

Now to start the .xinitrc file type `startx` or install [ly](https://github.com/fairyglade/ly)

You can install ly from the [AUR](https://aur.archlinux.org/packages/ly), using yay for example:

```
$ yay -S ly
```

Once the compilation is complete, run the command below to enable ly

`systemctl enable ly.service`

</br></br>


#### Configuration

You can find all the configuration in `/etc/ly/config.ini`. The file is commented, and includes the default values.

Now reboot

</br></br>

---
### Post install pt.2

- Install [BetterDiscord](https://betterdiscord.app/) - appimage
- Install [Spicetify](https://spicetify.app/docs/getting-started) - terminal
- Install [packer.nvim](https://github.com/wbthomason/packer.nvim) - yay
- Desktop Theming

### Neovim Configuration

![](https://i.imgur.com/BmilYtB.png)



Clone the repo

```bash
git clone https://github.com/jojihatzz/nvim-config
```

copy the contents of the folder to `/home/$USER/.config/nvim/`

Comment out the colorscheme file in the init.lua file and run :Packersync

```lua
----------------------------
require("user.options")
require("user.keymaps")
--require("user.colorschemes")
require("user.plugins")


-- Plugins
require("user.lsp.lsp_config")
require("user.lsp.mason_config")
require("user.telescope")
require("user.noice")
require("user.notify")
require("user.dashboard")
require("user.lualine")
require("user.toggleterm")
require("user.nvim-tree")
require("user.treesitter")
require("user.cmp")
```

close neovim and run again :Packersync.

Uncomment colorscheme file


</br></br>

---