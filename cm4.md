# cm4


[Mini Base Board (A) für Raspberry Pi Compute Module 4 | Mini Base Board (A) für Raspberry Pi Compute Module 4 - Erweiterungsboards | Raspberry Pi Mikrocontroller - Raspberry Pi | BerryBase](https://www.berrybase.de/raspberry-pi/raspberry-pi-mikrocontroller/erweiterungsboards/mini-base-board-40-a-41-f-252-r-raspberry-pi-compute-module-4)





[CM4-IO-BASE-A - Waveshare Wiki](https://www.waveshare.com/wiki/CM4-IO-BASE-A)

1: It is forbidden to unplug and plug any equipment other than USB and HDMI when power is on  
2: FAN fans only support 5V fans. 12V is not supported. Confirm the fan voltage before connecting. This version of the fan does not have a controller and cannot be adjusted in speed.  
3: The DSI display interface is the DSI0 interface, and the DSI1 display interface is not connected.  
4: Type C interface can be used for power supply or USB SLAVE interface for burning image.  
5: In order to ensure the normal power supply of CM4, please do not connect other devices when using the Type C interface to burn the image.  
6: When CM4 is in normal use, it needs to provide 5V 2A power supply for CM4. Otherwise, problems such as automatic shutdown, frequency reduction, etc. may occur.  
7: When using the M.2 interface, please use the matching screws. Using screws of other lengths may cause the CM4 core to be damaged by the screws.  
8: The module does not have any protection, please do not short-circuit the power supply.  
9: USB2.0 is closed by default, if you need to open it, you need to add dtoverlay=dwc2,dr\_mode=host  
10: If you want to use HDMI1 alone, you can purchase it separately if you need to use it [HDMI Adapter](https://www.waveshare.net/shop/HDMI-Adapter-Horizontal.htm)  
11: Both USB 3/4 and HDMI1 need to be used, you can use [adapter board](https://www.waveshare.net/shop/USB-HDMI-Adapter.htm) to connect it out  
12: This expansion board does not support the POE function.  
13: M.2 interface power supply is limited to 1.5A, if it causes problems such as slowing down of solid state or other equipment, it is recommended to buy version B




[CM4-IO-BASE-A - Waveshare Wiki](https://www.waveshare.com/wiki/CM4-IO-BASE-A)

No.

Component

Description

1 CM4 connector

Suitable for all versions of Compute Module 4

2 DC power supply/programming interface

5V/2.5A power supply, also can be used as eMMC programming interface

3 DISP Interface

MIPI DSI Display interface

4 FAN Interface

For connecting cooling fan, allows speed adjustment and measuremen, only support 5V fan.

5 CAM Interface

Dual MIPI CSI camera interface

6 HDMI0 Interface

HDMI Interface，Support 4K 30fps output

7 USB 2.0 Interface

2-channel USB 2.0 Interface, for connecting sorts of USB devices

8 Gigabit Ethernet

Gigabit Ethernet RJ45 connector, with 10 / 100 / 1000M network support

9 M.2 indicators

Indicating the operating status of M.2 interface

10 ACT indicators

Raspberry Pi operating status indicator

11 PWR indicators

Raspberry Pi power indicator

12 BOOT selection

jumper shorted: CM4 would be booted from USB-C interface  
jumper opened: CM4 would be booted from eMMC or Micro SD card

13 40PIN GPIO Interface

Conveniently connect various HAT modules

14 Micro SD Card interface

For connecting a Micro SD card with pre-burnt image (Lite variant ONLY).

15 HDMI1 interface

HDMI1 Interface，Support 4K 30fps output

16 USB 2.0 interface

Can be connected through an adapter

17 FE1.1S

USB HUB chip, expanding one USB port to 4x ports

18 M.2 Interface

Supports sorts of NVME SSD, or communication modules with PCIE M.2 KEY-M interface

  

  


## Writing Image

-   [Write Image for Compute Module Boards eMMC version](https://www.waveshare.com/wiki/Write_Image_for_Compute_Module_Boards_eMMC_version "Write Image for Compute Module Boards eMMC version")
-   [Write Image for Compute Module Boards Lite version](https://www.waveshare.com/wiki/Wrote_Image_for_Compute_Module_Boards_Lite_version "Wrote Image for Compute Module Boards Lite version")

## USB2.0

In order to save power, the USB interface of the CM4 is disabled by default. If you need to open the USB interface, please add the following line to the end of the config.txt:

dtoverlay=dwc2,dr\_mode=host

And then reboot the system.

## FAN

The PWM pin of the FAN is connected to the GPIO18 of the CM4 board.

## CSI DSI

CSI and DSI are disabled by default. When using the camera and DSI, it will occupy three I2C devices: I2C-10, I2C-11, and I2C-0.  

-   Open a terminal and run the following commands:  
    

 sudo apt\-get install p7zip\-full
 wget https://www.waveshare.com/w/upload/4/41/CM4\_dt\_blob.7z
 7z x CM4\_dt\_blob.7z \-O./CM4\_dt\_blob
 sudo chmod 777 \-R CM4\_dt\_blob
 cd CM4\_dt\_blob/
 #If you want to use both cameras and DSI0
 sudo  dtc \-I dts \-O dtb \-o /boot/dt\-blob.bin dt\-blob\-disp0\-double\_cam.dts
 #If you want to ue both cameras and DSI1
 sudo  dtc \-I dts \-O dtb \-o /boot/dt\-blob.bin dt\-blob\-disp1\-double\_cam.dts

-   And then connect the cameras and DSI display  
    

1: Please power off the IO Board first before your connection.  
2: Connect the power adapter after connecting the cameras and DSI display  
3: Wait a few seconds before the screen boot up.  
4: If the DSI LCD cannot display, please check if you have added /boot/dt-blob.bin. If there already has the dt-blob.bin, just try to reboot.  
5: The camera needs to be enabled by raspi-config, enter sudo raspi-config on the terminal, choose Interfacing Options->Camera->Yes->Finish-Yes and reboot the system  

-   Test the Cameras:  
    

Test camera0:

sudo raspivid -t 0 -cs 0

Test camera1:

sudo raspivid -t 0 -cs 1

【Note】:  

-   HDMI1 is disabled if you use DSI interfaces for displaying, even if you just compile the corresponding files without connecting to the DSI screen, please note it.
-   If you want to enable the HDMI1, please remove the dt-blob.bin file with the command:

sudo rm -rf /boot/dt-blob.bin

And then turn off IO Board and reboot it.
