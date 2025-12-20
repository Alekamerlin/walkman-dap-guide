# Walkman DAP Guide

A user friendly guide to using Walkman DAP players.

### NW-A50 (NW-A55/NW-A56/NW-A57)

#### Knowledge base:

Resources:
- [Offical user manual from SONY](https://helpguide.sony.net/dmp/nwa50/v1/en/index.html)
- [About Walkman A series on Wikipedia](https://en.wikipedia.org/wiki/Walkman_A_Series)
- [Destination and sounds pressure tool](https://www.rockbox.org/wiki/SonyNWDestTool)
- [About a bug with the destination and sounds pressure tool](https://forums.rockbox.org/index.php?topic=54610.0)

#### About the device

The **NW-A50** is a series of the digital audio players from SONY that [sound pretty well](https://www.youtube.com/watch?v=Rwal4qYWgK8). The difference between the models in the line is in the storage capacity and regional settings, such as the interface language and FM radio band. Some features, such as ATRAC support, may or may not be available in the device.

The Walkman's storage can be expanded [up to 1TB](https://www.sony.ca/en/electronics/support/digital-music-players-nw-nwz-a-series/nw-a55/articles/00200481) with an SD Card, so even for DSD files, the player is a capacious device.

#### About the Walkman's firmware

It seems that all the players in the line have the same firmware with different settings for each region. The region settings are determined by the destination code. There's an unofficial tool that can change the destination code, so it's possible to reprogram a Walkman from one region to another.

The firmware is not based on Android, so there's no online streaming and other Android features, but the player can work as a DAC for a PC or a Bluetooth reciever.

#### The Walkman's features

The main feature of the **NW-A50** is [the playback of music files](https://helpguide.sony.net/dmp/nwa50/v1/en/contents/TP0002342858.html) from the built-in storage or SD Card. In addition to music files, the player [can play language learning files](https://helpguide.sony.net/dmp/nwa50/v1/en/contents/TP0002342877.html) (regular audio files from the learning direcory) and [listen to FM radio](https://helpguide.sony.net/dmp/nwa50/v1/en/contents/TP0002342923.html). The player can also [work as a DAC](https://helpguide.sony.net/dmp/nwa50/v1/en/contents/TP0002347800.html) (digital audio convertor) for a PC via a USB connection or as [a Bluetooth reciever](https://helpguide.sony.net/dmp/nwa50/v1/en/contents/TP0002348531.html).

There are also many features to adjust the sound quality, such as [equalizer](https://helpguide.sony.net/dmp/nwa50/v1/en/contents/TP0002342874.html), [noise cancellation](https://helpguide.sony.net/dmp/nwa50/v1/en/contents/TP0002342875.html), [ambient sound](https://helpguide.sony.net/dmp/nwa50/v1/en/contents/TP0002348599.html), etc.

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

#### Change the region and sounds pressure of the Walkman

Find a suitable region (destination code) in the table at the bottom of [the page](https://www.rockbox.org/wiki/SonyNWDestTool).

Set the destination code and disable the sounds pressure, using the command:
```
$ /path_to_the_tool/scsitool_64-nwz-v27 /dev/sdb -c dest_tool set U off
```
Where `U` is the destination code for the US region, and `off` disables sounds pressure.

After changing the destination code, disconnect the Walkman, and reset it to factory settings to apply the changes.
