# Dynamic Resolution For Debian
---

## Installation
---
Copy the binary file in the bin folder and paste it in the `/usr/local/bin directory`:
```bash
    cp /path/to/this/repo/bin/x-resize /usr/local/bin
```

Then copy the udev rule file in `/etc/udev/rules.d`:
```bash
    cp /path/to/this/repo/udev/50-x-resize.rules /etc/udev/rules.d
```

Reload the udev rules with:
```bash
    sudo udevadm control --reload-rules
```

Make sure you have installed: `qemu-guest-agent` `spice-vdagent` `xserver-xspice` `xserver-xorg-video-qxl`.

Make sure also spice-vdagent is up and running;
```bash
    sudo systemctl status spice-vdagentd
```
Activate your `Active resize VM with window` option on your virtual manager and it should scale accordingly.

## Debugging 
Watch udev events as you are resizing:
```bash
    udevadm monitor --subsystem-match=drm --property
```

This is primarly made for kali but it should work on all distros with XFCE since there is a known bug that ignores the driver for autoresolution for atleast `virt-manager`

Btw if none of this helps somehow here is the manual version for autoresolution

```bash
    xrandr --output Virtual-1 --auto
```

## Credits 
Credits for making the binary: https://gist.github.com/3lpsy/4cc344ae031bf77595991c536cbd3275
