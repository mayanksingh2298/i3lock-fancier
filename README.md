# i3lock - modified

This fork builds over [SuperPrower/i3lock-fancier](https://github.com/SuperPrower/i3lock-fancier) which originally combined features of [i3lock-color](https://github.com/chrjguill/i3lock-color)
and [this i3lock fork](https://github.com/cac03/i3lock/commits/master) to
create my ultimate lockscreen experience.


## Features:
* will set up keyboard shortcuts and terminal aliases
* the lockscreen's background is your current blurry screen
* shows time and date
* separated configuration variables and more cleaner code in future
* loading configurations from .ini config files with [this library](https://github.com/rxi/ini)
* keyboard indicator and Caps Lock layout:

![Feature showcase](https://github.com/mayanksingh2298/i3lock-fancier/blob/master/screenshot.png)

## Pre-reqs: 
`sudo apt install pkg-config libxcb1 libpam-dev libcairo2-dev libxcb-composite0 libxcb-composite0-dev libxcb-xinerama0-dev libev-dev libx11-dev libx11-xcb-dev libxkbcommon0 libxkbcommon-x11-0 libxcb-dpms0-dev libxcb-image0-dev libxcb-util0-dev libxcb-xkb-dev libxkbfile-dev libxkbcommon-x11-dev libxkbcommon-dev imagemagick scrot`

## Let me set you up:
1. Run the following commands in a terminal:
```bash
git clone https://github.com/mayanksingh2298/i3lock-fancier
cd i3lock-fancier
sudo make install
mkdir ~/.config/i3lock-fancier
cp test_config.ini ~/.config/i3lock-fancier/config.ini
```
3. Create a script `i3_blur_lock.sh` in /bin and fill it with the following code
```bash
PICTURE=~/.config/i3lock-fancier/i3lock.png
BLUR="5x4"
scrot $PICTURE
convert $PICTURE -blur $BLUR $PICTURE
i3lock
rm $PICTURE
```
4. Give it execute permission by typing in:
```bash
sudo chmod +x /bin/i3_blur_lock.sh
```
5. Now go to keyboard settings > shortcuts
6. Add a custom shortcut which launches when you press Super + L and has command `i3_blur_lock.sh`. (You may have to disable the original binding of Super+L)
7. Optionally you can add the following at the end of ~/.bashrc
```bash
#blurry screen lock
lock(){
	PICTURE=~/.config/i3lock-fancier/i3lock.png
	BLUR="5x4"

	scrot $PICTURE
	convert $PICTURE -blur $BLUR $PICTURE
	i3lock
	rm $PICTURE	
}
```
8. That's it guys, now you can lock your screen by hitting Super+L or typing lock in your terminal
9. Tune `$HOME/.config/i3lock-fancier/config.ini` as per your needs.

## Keep in mind:
* I don't know how to work with OpenBSD, so I removed all BSD-related code

