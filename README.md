<h1 align="center">Useful guide for debian users</h1>

## Show git branch name in bash terminal path

1. Open a terminal and run the command:

```
git config --global log.decorate auto
```

2. Next, find the following lines in your .bashrc:

```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
```

3. Replace it with:

```
parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}

if [ "$color_prompt" = yes ]; then
   PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[m\]:\[\033[01;94m\]\w\[\e[93m\]$(parse_git_branch)\[\033[00m\]\$ '
else
   PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w$(parse_git_branch)\$ '
fi
```

<h2 style="color: #4CB9E7"> Enable/Disable Gnome Shell Activities Animations: </h2>

To <b style="color: #FFC300"><i> enable </i></b> activities animations run:

```
gsettings set org.gnome.desktop.interface enable-animations true
```

or <b style="color: #FFC300"><i> reset </i></b> to default settings:

###### Animation is enabled by default

```
gsettings reset org.gnome.desktop.interface enable-animations
```

To <b style="color: #FFC300"><i> disable </i></b> activities animations run:

```
gsettings set org.gnome.desktop.interface enable-animations false
```

### Or you can run activities-animations

To <b style="color: #FFC300"><i> enable </i></b> activities animations run:

```
bash activities-animations on/true
```

To <b style="color: #FFC300"><i> disable </i></b> activities animations run:

```
bash activities-animations off/false
```

<h2 style="color: #4CB9E7"> To change the cursor size: </h2>

To <b style="color: #FFC300"><i> change </i></b> the cursor size run:

```
gsettings set org.gnome.desktop.interface cursor-size "size"
```

To <b style="color: #FFC300"><i> reset </i></b> the cursor size run:

```
gsettings reset org.gnome.desktop.interface cursor-size
```

To <b style="color: #FFC300"><i> get </i></b> the current cursor size run:

```
gsettings get org.gnome.desktop.interface cursor-size
```

### Or you can run cursor-size

To <b style="color: #FFC300"><i> change </i></b> the cursor size run:

```
bash cursor-size "size"
```

To <b style="color: #FFC300"><i> reset </i></b> the cursor size run:

```
bash cursor-size reset
```

To <b style="color: #FFC300"><i> get </i></b> the current cursor size run:

```
bash cursor-size
```
## FFMPEG Converting
1. Install ffmpeg

```
sudo apt install ffmpeg
```
2. Converting from mp4 to webm
```
ffmpeg -i input.mp4 -c:v libvpx-vp9 -crf 30 -b:v 0 -b:a 128k -c:a libopus output.webm
```
