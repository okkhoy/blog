# `rsync`

`rsync` is an indispensable tool to back up data to any device - be it an external disk, cloud storage or a network drive.
There are a few versions/applications that wrap around `rsync` for Windows, but I am happy to use it from my Linux partition.

In most cases, the following basic command works very well when backing up to external drives (formatted as NTFS or FAT drives) 
or network locations.

    rsync -avP source/ destination
    
The flag `-a` (stands for archive) is a substitute for `rlptgoD` switches; `-v` makes the operations verbose, showing you a
lot of screen output of what is happening and `-P` enables partial sync (and shows progress), so that you can resume if 
sync fails at any time.

Notice the trailing `/` after `source`? That means, sync "contents of source" into the destination. Without the trailing `/`, 
`rsync` creates a folder called `source` under the `destination`.

If you have formatted the external drive (or any media for that matter) as `exFAT` you need to take care of a couple of things.

- You need to install `exfat-fuse` and `exfat-utils` on the linux machine to be able to mount the drive. 
[Source](http://askubuntu.com/a/114648/84408)
  - `sudo apt-get install exfat-utils exfat-fuse`
    
- Next, `exFAT` doesn't support permissions, hence, using `-a` flag fails with `function not implemented` error. 
To overcome this, we need to remove `pgo` switches and explicitly specify the flags for `rsync`.
  - `rsync -rltDvP source/ destination`
  
# Touchpad troubles in Ubuntu

It is quite annoying when you are typing and accidentally the cursor moves haywire because your palm contacted the touch pad. I wanted to disable the touchpad completely when I type.
On a Ubuntu machine you can do the following.

- First get a list of all input devices
  `xinput list`
- It shoud show the output similar to below

```
    ⎡ Virtual core pointer                    	id=2	[master pointer  (3)]
    ⎜   ↳ Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
    ⎜   ↳ DualPoint Stick                         	id=13	[slave  pointer  (2)]
    ⎜   ↳ Logitech USB Receiver                   	id=16	[slave  pointer  (2)]
    ⎜   ↳ AlpsPS/2 ALPS DualPoint TouchPad        	id=12	[slave  pointer  (2)]
    ⎣ Virtual core keyboard                   	id=3	[master keyboard (2)]
        ↳ Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
        ↳ Power Button                            	id=6	[slave  keyboard (3)]
        ↳ Video Bus                               	id=7	[slave  keyboard (3)]
        ↳ Power Button                            	id=8	[slave  keyboard (3)]
        ↳ Sleep Button                            	id=9	[slave  keyboard (3)]
        ↳ Laptop_Integrated_Webcam_HD             	id=10	[slave  keyboard (3)]
        ↳ AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
        ↳ Dell WMI hotkeys                        	id=14	[slave  keyboard (3)]
        ↳ Logitech USB Receiver                   	id=15	[slave  keyboard (3)]
```
- Get the id of the touch pad (here it is 12)
- Now disable the touch pad using the command below
  `xinput set-prop 12 "Device Enabled" 0`
  OR
  `xinput --disable 12`

- To re-enable the touch pad, you can set the flag to 1 as shown:
  `xinput set-prop 12 "Device Enabled" 1`
  OR
  `xinput --enable 12`

