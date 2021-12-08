# rpi4.apitoy.com - install, develop


## OS



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
