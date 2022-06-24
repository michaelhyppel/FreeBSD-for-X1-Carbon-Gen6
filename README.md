# Installing FreeBSD 13.1 on a Lenovo Thinkpad X1 Carbon

This guide is made for the 6th gen X1 (20KH) and FreeBSD 13.1-RELEASE.

Firmware updates prior to installing:

* BIOS version 1.56 (Released 
* Synaptics Touchpad Firmware PR2698617/PR281276 (Released 04 Dec 2018)
* TrackPoint Firmware 1.0.0.3 (Released 07 Nov 2018)

## Trackpoint and Trackpad

Install moused during install.

## ACPI support for suspending, lcd etc

Add these lines to /boot/loader.conf
```
acpi_video_load="YES"
acpi_ibm_load="YES"
```

Add this line to /etc/sysctl.conf
```
hw.acpi.lid_switch_state=S3
```

## Packages

```
pkg install git vim neofetch tmux
```

## Xorg and KDE Plasma

```
pkg install xorg plasma5-plasma firefox konsole networkmgr
```

### Install graphics driver

```
pkg install drm-kmod
sysrc -f /etc/rc.conf kld_list+=i915kms
pw usermod ${USERNAME} -G video
```

### Configure X

Create a file for keyboard layout
```
vim /usr/local/etc/X11/xorg.conf.d/keyboard-se.conf

Section "InputClass"
  Identifier      "KeyboardDefaults"
  MatchIsKeyboard "on"
  Option          "XkbLayout" "se"
 EndSection
 ```

### Configurations for KDE Plasma

Add these lines to /etc/rc.conf
```
dbus_enable="YES"
```

Add this line to ~/.xinitrc for starting Plasma with startx
```
exec ck-launch-session startplasma-x11
```

## Nice to have packages

```
pkg install brasero libreoffice kdenetwork
```
