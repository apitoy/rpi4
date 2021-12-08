# rpi4.apitoy.com - install, develop


## OS


[Raspberry Pi Documentation - The config.txt file](https://www.raspberrypi.com/documentation/computers/config_txt.html)




## Config.txt


## What is `config.txt`?

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/config_txt/what_is_config_txt.adoc)

The Raspberry Pi uses a configuration file instead of the [BIOS](https://en.wikipedia.org/wiki/BIOS) you would expect to find on a conventional PC. The system configuration parameters, which would traditionally be edited and stored using a BIOS, are stored instead in an optional text file named `config.txt`. This is read by the GPU before the ARM CPU and Linux are initialised. It must therefore be located on the first (boot) partition of your SD card, alongside `bootcode.bin` and `start.elf`. This file is normally accessible as `/boot/config.txt` from Linux, and must be edited as [root](https://www.raspberrypi.com/documentation/computers/using_linux.html#root-and-sudo). From Windows or OS X it is visible as a file in the only accessible part of the card. If you need to apply some of the config settings below, but you don’t have a `config.txt` on your boot partition yet, simply create it as a new text file.

Any changes will only take effect after you have rebooted your Raspberry Pi. After Linux has booted, you can view the current active settings using the following commands:

-   `vcgencmd get_config <config>`: this displays a specific config value, e.g. `vcgencmd get_config arm_freq`.
    
-   `vcgencmd get_config int`: this lists all the integer config options that are set (non-zero).
    
-   `vcgencmd get_config str`: this lists all the string config options that are set (non-null).
    

Note

There are some config settings that cannot be retrieved using `vcgencmd`.

### [](https://www.raspberrypi.com/documentation/computers/config_txt.html#file-format)File Format

The `config.txt` file is read by the early-stage boot firmware, so it has a very simple file format. The format is a single `property=value` statement on each line, where `value` is either an integer or a string. Comments may be added, or existing config values may be commented out and disabled, by starting a line with the `#` character.

There is a 98-character line length limit (previously 78) for entries - any characters past this limit will be ignored.

Here is an example file:

Copy to Clipboard

\# Enable audio (loads snd\_bcm2835)
dtparam=audio=on

# Automatically load overlays for detected cameras
camera\_auto\_detect=1

# Automatically load overlays for detected DSI displays
display\_auto\_detect=1

# Enable DRM VC4 V3D driver
dtoverlay=vc4-kms-v3d
max\_framebuffers=2

# Disable compensation for displays with overscan
disable\_overscan=1

### [](https://www.raspberrypi.com/documentation/computers/config_txt.html#advanced-features)Advanced Features

#### [](https://www.raspberrypi.com/documentation/computers/config_txt.html#include)`include`

Causes the content of the specified file to be inserted into the current file.

For example, adding the line `include extraconfig.txt` to `config.txt` will include the content of `extraconfig.txt` file in the `config.txt` file.

**Include directives are not supported by bootcode.bin or the EEPROM bootloader**

#### [](https://www.raspberrypi.com/documentation/computers/config_txt.html#conditional-filters)Conditional Filters

Conditional filters are covered in the [conditionals section](https://www.raspberrypi.com/documentation/computers/config_txt.html#conditional-filters).


## Config.txt


The `config.txt` file is used to configure boot and hardware configuration on Raspberry Pi hardware, similar to how the "BIOS" is used on an Intel PC.
 

Edit via SSH

## Raspberry OS

### [Raspbian](https://www.raspbian.org/) 

    /dev/config.txt

### [Ubuntu for Raspberry Pi | Ubuntu](https://ubuntu.com/raspberry-pi)
  
    /dev/firmware/config.txt
    

The `/flash` boot partition is read-only by default, so we need to remount it in read-write mode:

    mount -o remount,rw /flash

Use the `nano` text editor to modify the file. Save changes with `ctrl+o` and exit using `ctrl+x`:

    nano /flash/config.txt

After editing set the `/flash` partition back to read-only mode:

    mount -o remount,ro /flash

And reboot for the changes in `config.txt` to be applied:

    reboot

Edit via Card Reader
