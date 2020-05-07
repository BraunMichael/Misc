### Fix for ubuntu/windows times being different from [here](https://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot):
```
timedatectl set-local-rtc 1
```

### Possibly useful for fixing infinite login loop:
```
cd ~
vim .profile
-use "i" to start editing, add the following lines:
export DISPLAY=:0
-then hit esc and type :wq and hit enter
source .profile
```

### Nice programs, install using the commands below: psensor, notepadqq, pycharm, [audio-output-switcher](https://github.com/adaxi/audio-output-switcher), solaar, [flameshot](https://github.com/lupoDharkael/flameshot)
```
sudo snap install pycharm-community --classic
sudo snap install --classic notepadqq
sudo apt-add-repository ppa:jfi/ppa
sudo apt-get update
sudo apt-get install indicator-sound-switcher lm-sensors psensor solaar flameshot
```

For audio switching, either sound switcher indicator or the gnome extension [audio-output-switcher](https://github.com/adaxi/audio-output-switcher).

For [audio-output-switcher](https://github.com/adaxi/audio-output-switcher) (Preferred):
```
sudo apt install gnome-tweaks gnome-shell-extensions
git clone https://github.com/adaxi/audio-output-switcher.git ~/.local/share/gnome-shell/extensions/audio-output-switcher@anduchs
```

Then Alt + f2, r, then go to tweaks and enable it

For sound switcher indicator
```
sudo apt-add-repository ppa:yktooo/ppa
sudo apt-get install indicator-sound-switcher
```

GPU Monitor:
```
sudo apt install flatpak gir1.2-appindicator3-0.1
flatpak --user remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak --user install flathub com.leinardi.gwe
flatpak update 
```
Restart computer
```
sudo nvidia-xconfig --cool-bits=12
flatpak run com.leinardi.gwe
```

Get icon for it and put it in a convenient folder for the next step
```
wget https://gitlab.com/leinardi/gwe/-/raw/release/data/icons/hicolor/48x48@2x/apps/com.leinardi.gwe.png
sudo mv ./com.leinardi.gwe.png /usr/share/app-install/desktop
```
Can make a .desktop file with the below contents, put on desktop, right click and make launchable to launch it.
```
[Desktop Entry]
Version=1
Name=GWE Monitor
Comment=Terminal Desktop Shortcut
Exec=flatpak run com.leinardi.gwe
Icon=/usr/share/app-install/desktop/com.leinardi.gwe.png
Terminal=false
Type=Application
Categories=Application
```

For Flameshot screenshots, change default Ubuntu screenshot shortcut to Flameshot by going to settings - keyboard shortcuts, then disabling the default shortcut. Then scroll all the way down and click the '+' to add a custom shortcut. For the command enter:
```
flameshot gui
```
Remember that you may have to press fn + print screen depending on your keyboard!

### Nice tidbits:
Use Shift + volume +/- for a finer control of volume
[Fix the photo viewer blurring](https://askubuntu.com/questions/237575/zoom-in-on-small-photos-without-losing-pixel-crispness) by going to image viewer preferences on an open image - Image Enhancements - uncheck the Smooth Images options


Nvidia Issues?
Get graphics driver directly from site [here](https://www.nvidia.com/Download/index.aspx).
