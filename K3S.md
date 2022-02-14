[Install K3S On Raspberry Pi [Complete Setup]](https://360techexplorer.com/install-k3s-on-raspberry-pi/)

### 1: Setup Raspberry Pi SSH

1.  Plug your SDCard into your micro SDCard adapter.
2.  Now plug the adapter into your main PC.
3.  Download Raspberry Pi imager from their [download page](https://www.raspberrypi.org/software/).
4.  Open Raspberry Pi imager
5.  Click on “Choose Image” and then “Raspberry Pi OS (other)”
6.  Then choose “Raspberry Pi OS lite”
7.  Now choose your micro SDCard by clicking “Choose Storage”
8.  Then click on write, (confirm the write by click on yes)
9.  When it finishes remove your SDCard from your computer and plug it into your Raspberry Pi.
10.  Boot your Raspberry Pi
11.  Wait (5 min) to boot up Raspberry Pi.
12.  Now again unplug the SDCard from Raspberry Pi and plug it back into your computer.
13.  This time when you plug this SDCard into your PC you see a “Boot” disk, open it
14.  Here look for the “cmdline.txt” file and open it with your perfected text editor.
15.  Add the following line to the end of the line.

    cgroup_memory=1 cgroup_enable=memory ip=[ENTER_AN_IP_FOR_YOUR_RASPBERRY_PI]::[DEFULT_GATEWAY]:[SUBNET_MASK]:[NAME_FOR_RASPBERRY_PI]:[NETWORK_INTERFACE]:off
    
    
    
    E.g: 
    cgroup_memory=1 cgroup_enable=memory ip=192.168.1.10::192.168.1.1:255.255.255.0:rpimaster:eth0:off

16.  Save this file and close
17.  Open another file labeled “config.txt”
18.  Add the following line to the button of the file.

    arm_64bit=1

19.  Save this file and close

_Now one last thing is to enable SSH on Raspberry Pi_ 

20.  To do that open Powershell in windows and terminal in Linux and Mac.
21.  Navigate to the “boot” drive
22.  Exclude the following command

    # For windows
    new-item ssh
    
    
    # For Linux and Mac
    touch ssh

23.  Unplug the micro SDCard from the PC and plug it into your Raspberry Pi .
24.  Boot the Raspberry Pi
