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

## Packages

```
pkg install git vim neofetch tmux
```

## Xorg and KDE Plasma

```
pkg install xorg plamsa5-plasma firefox alacritty
```

### Install graphics driver

```
pkg install drm-kmod
sysrc -f /etc/rc.conf kld_list+=i915kms
pw usermod ${USERNAME} -G video
```

## Nice to have packages

```
pkg install brasero libreoffice
```
