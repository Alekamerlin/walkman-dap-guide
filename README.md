# Walkman DAP Guide

A user friendly guide to using Walkman DAP players.

### NW-A50 (NW-A55/NW-A56/NW-A57)

#### Knowledge base:

Resources:
- [Offical user manual from SONY](https://helpguide.sony.net/dmp/nwa50/v1/en/index.html)
- [About Walkman A series on Wikipedia](https://www.rockbox.org/wiki/SonyNWDestTool)
- [Destination and sounds pressure tool](https://en.wikipedia.org/wiki/Walkman_A_Series)
- [About a bug with the destination and sounds pressure tool](https://forums.rockbox.org/index.php?topic=54610.0)

#### How to get info about the Walkman

Get the tool [here](https://www.rockbox.org/realwiki/pub/Main/SonyNWDestTool/scsitool_64-nwz-v27) and unpack it. The file should be `scsitool_64-nwz-v27`, where `_64` is the platform name while `-v27` is the tool version.

Connect a Walkman to the PC and find the path to it, using the command:
```
# fdisk -l
```
> From now on `#` describes that the command should be called as root, while `$` describes that the command should be called from a regular user.
```
$ /path_to_the_tool/scsitool_64-nwz-v27 /dev/sdb -c dest_tool get
```
> Use the `-c` key to disable color output as there is a bug.

If the output is something like "Cannot open device", try disconnecting and reconnecting the device.
