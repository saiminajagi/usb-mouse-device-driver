# usb-mouse-device-driver
Device Driver to adjust the screen brightness using mouse keys

 HOW TO RUN THE CODE

Using the device driver file :
  
  Run make command, this will create a .ko file which we will use to load the device driver

1. You need to register a device with a major number (same as in device driver code ) and minor number
   
   sudo mknod /dev/myDev c 91 1

2. Now remove the default usb driver (usbhid)
   
   sudo rmmod usbhid

3. Now your usb mouse should stop working. Now load our device driver
  
   sudo insmod usbmouse.ko

4. compile adjustBrightness_exiting.c .This file basically reads from /dev/myDev and adjusts brightness.
    
    gcc adjustBrightness_exiting.c

5. Now run the compiled file. On pressing left and right clicks, the brightness should change (the brightness file and values can 

be different for different machines. On our system the brightness varies from 1 to 4881 and the file is /sys/class/backligh 

/intel_backlight/brightness and the brightness increases by 244 for each jump ) and middle click exits the program.

  sudo​ ​ ./a.out

6. Removing our driver module

  sudo rmmod usbmouse

7. Loading default usb driver back
  
   sudo modprobe usbhid
