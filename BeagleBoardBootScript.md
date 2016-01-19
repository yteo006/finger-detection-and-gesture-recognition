#My BeagleBoard Boot script

I used a BeagleBoard-Xm for my thesis. Running Angstrom Distro, and S-Video as main display output.

```
led 1 off
mmc init
setenv mmcargs 'setenv bootargs console=${console} ${optargs} mpurate=${mpurate} buddy=${buddy} vram=${vram} omapfb.mode=tv:ntsc omapdss.def_disp=tv root=${mmcroot} rootfstype=${mmcrootfstype}'
run loaduimage
led 1 on
run mmcboot
```

For more about BeagleBoard, you should Visit its Page at http://www.Beagleboard.org