# Welcome to the .dotfiles of my Archlinux i3 laptop setup

From https://wiki.archlinux.org/title/I3 : i3 is a tiling window manager inspired by wmii that is primarily targeted at developers and advanced users. 

After using a combination of various other dotfiles from generous people on Github, combined with my own adjustments, I decided to share my current setup too.<BR />
I'm running Archlinux with i3 as my window manager both on my laptop and my Nuc.  This repository focuses on my laptop's configuretion. I used other people's dotfiles and adapted them to my desire.  Rofi is used as an application launcher.  Polybar is the bar on top.<BR />
<BR />
This repository contains my dotfiles in a .tar file which you can extract to your ~/.config folder.<BR />
<BR />
I also added a file called packages.txt containing all the packages I currently have installed.  If I ever break my system it can be a useful list to have.  You probably don't need all those packages.  Picom is used for some eyecandy.  Dunst is configured at the notification manager.  The lockscreen is a small script that creates a screenshot of the desktop, and then blurs that.  

# Tools to install besides Archlinux base install and i3

> Redshift<BR>
> Alacritty<BR>
> Termite<BR>
> Arandr / xrandr<BR>
> Lxappearance<BR>
> Bluez / bluez-utils<BR>
> Firefox<BR>
> i3lock<BR>
> Blurlocker<BR>
> Rofi<BR>
> Thunar<BR>
> Firefox<BR>
> Audacious<BR>
> Mate-power-manager<BR>
> NetworkManager + nm-applet<BR>
> Udiskie / udisks2<BR>
> Feh<BR>
> Xwallpaper<BR>
> Maim<BR>
> Dunst<BR>
> Picom<BR>
> Dex<BR>
> i3-scratchpad-git<BR>

# Important keyboard shortcuts

| Key(s) | Description |
| --- | --- |
| $mod | Mod4 (Windows key) |
| $mod+Left | Focus left |
| $mod+Right | Focus right |
| $mod+Down | Focus down |
| $mod+Up | Focus up |
| $mod+(1...9) | Switch to workspace (1...9) |
| $mod+Shift+(1...9) | Move window to workspace (1...9) |
| $mod+d | Rofi |
| $mod+Enter | Alacritty |
| Twosuperior | Termite Quake-style terminal |
| $mod+t | Thunar |
| $mod+b | Firefox |
| $mod+m | Audacious |
| $mod+q | Kill |
| $mod+r | Resize mode (use arrow keys to resize, then press ENTER or ESC) |
| $mod+v | Split vertically |
| $mod+b | Split horizontally | 
| prtsc | Screenshot (entire screen) |
| $mod+prtsc | Screenshot (selected window only) |
| Shift+prtsc | Screenshot (only selected part via mouse) |
| $mod+s | Layout stacking |
| $mod+e | Layout split |
| $mod+w | Layout tabbed |
| $mod+f | Full screen |
| $mod+Shift+Space | Toggle floating |
| $mod+Shift+Arrow key | Move window |
| $mod+Tab | Workspace next |
| mod+Shift+Tab | Workspace previous |
| $mod+l | Blurred lockscreen |


If your keyboard has multimedia keys such as play/pause, next, previous or volume keys they should work too.


# Scratchpad
One of the best features of tiling window managers is scratchpad.  I'm not going to explain in details what it is but you can consider it like an invisible workspace where you can send windows to and retrieve from.  Here are the keybinds that will make your life a whole lot easier.<BR />
Move to scratchpad : ```bindsym $mod+Shift+minus move scratchpad```<BR />
Toggle between windows in scratchpad : ```bindsym $mod+minus scratchpad show```<BR />
<BR>
This also allows for a Quake-style terminal.  Termite in dropdown mode is used for that.
Start Termite : ``` exec --no-startup-id termite --name dropdown &```<BR />
Bind to the twosuperior key : ``` bindsym twosuperior [instance="dropdown"] scratchpad show, move position center ```<BR />
Define the dropdown properties : ```for_window [instance="dropdown"] floating enable, resize set 1300 1000, move scratchpad ```<BR />


# Auto-mount external hard drives
I prefer my USB connected external hard drives to be mounted automatically.  For this I installed ```udisks2``` which is enabled at boot via ```systemctl enable --now udisks2.service```.  As for automount I prefer ```udiskie``` which is autostarted with i3 via ```exec --no-startup-id udiskie --tray``` in my ~/.config/i3/config file.

# Automatic Timeshift backups
Timeshift is a very useful tool to automatically create backups of your device.   It can be installed from AUR (```extra/timeshift 24.06.3-1 ``` at the time of writing).  To launch it in i3 enter ```sudo -E timeshift-gtk```. <BR />
Archlinux does come with cronie installed by default, but it's not started at boot.  Enter ```sudo systemctl enable --now cronie && systemctl enable --now cronie.service```.  Timeshift will now create automatic backups based on your preferences.  This can be daily, hourly, at boot,...  Yes, I'm well aware of the pacman hooks that allow for btrfs snapshots before updating too.  I just prefer this method.<BR />

# Show me!
Clean:
![Clean desktop.](https://github.com/himselfish/i3-dotfiles/blob/main/clean.png)

Busy:
![Busy desktop.](https://github.com/himselfish/i3-dotfiles/blob/main/fake_busy.png)

