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
