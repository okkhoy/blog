# Android hacks

## `rsync` Android files

- Purpose:
	- To backup files on Android phone (internal memory and SD card).
- Problem:
	- Google stopped support for mounting Android devices as usb devices starting Android 4.
	- Currently Android devices are mounted as media devices using MTP.
	- **Question:** How to mount/run `rsync` MTP devices over USB?
- Solution:
	- On Linux machines, MTP devices are mounted under `gvfs`
	- Get the location of the mounted devices 
		- Usually under: `/run/user/$UID/gvfs`
	- Change directory to which folder you want to `rsync`
		- `cd /run/user/$UID/gvfs/mtp*` 
		- if there are multiple devices mounted, using `mtp*` won't help
		- need to check and `cd` to the right directory
	- Run `rsync` as below:
	- `rsync --verbose --progress --omit-dir-times --no-perms --recursive --inplace --size-only /run/user/1000/gvfs/<mtp*>/<folder>/ <Target>`
- Important:
	- `--inplace` will copy the files in place and prevent duplication
	- `--omit-dir-times` and `--no-perms` are required since MTP doesn't support syncing those parameters
	- `--size-only` reduces the sync to directory listing and not checksums
	- Another option is to use `--ignore-existing` which ignores the files already present in target
- Issues:
	- On some devices/some cards, transfer can be excruciatingly slow
	- (Based on experience)

Source: [askubuntu](http://askubuntu.com/a/789898/84408)