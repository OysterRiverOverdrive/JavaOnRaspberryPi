# JavaOnRaspberryPi
Notes about how to setup and use a raspberry pi as a place to test Java code when a full robot/roborio is not available.

## Supplies

* Raspberry Pi (A [Raspberry Pi 3B](https://www.raspberrypi.com/products/raspberry-pi-3-model-b/) was used for generating this tutorial).
* A micro SD card.
* A micro SD card adapter (if your computer doesn't have a non-micro SD card slot).
* Micro USB power supply. This can be just a standard micro SD cable plugged into a USB port.
* Monitor with HDMI (most raspberry pis have an HDMI output but check to be sure).
* USB keyboard and mouse.

## Installing the Operating System

Installing an operating sysetem (OS) onto an SD card is also known as "flashing" the SD card. What's happening here is that we're downloding a copy of the files and folders/directories that should be written to the disk (referred to as a "disk image"), and overwriting whatever may have existed on the disk/card before with the new files.

Below are two installation options:

* General Installation - Use this one if you're not sure.
* Linux CLI-based Installation - For advanced users.

### General Installation

The Raspberry Pi website has up to date documentation on how to install the OS from a variety of computers.  Follow the directions in https://www.raspberrypi.com/software/ to install the OS.

### Linux CLI-based Installation

The following commands are run from a linux terminal. (Generally started by pressing CTRL+ALT+t)

Download the compressed image.

```
curl -L -o raspios.img.xz https://downloads.raspberrypi.org/raspios_lite_arm64/images/raspios_lite_arm64-2022-09-26/2022-09-22-raspios-bullseye-arm64-lite.img.xz
```

This should download the 64bit image from https://downloads.raspberrypi.org/raspios_lite_arm64/images/ (Feel free to update date in the command to a more recent image.)

Extract the image.

```
unxz raspios.img.xz
```

If you get `command not found: unxz`, you'll need to install the utility. Possibly with `sudo apt install xz-utils`.

Find the SD card device.  If you're unsure, run `sudo fdisk -l` before and after inserting the SD card and find the new one.  The device should be `/dev/something` like `/dev/mmcblk0` or `/dev/sdc1`.  BE CAREFUL THAT YOU CHOOSE THE CORRECT DEVICE OR YOU COULD OVERWRITE THE WRONG THING.

```
sudo dd if=raspios.img of=/dev/mmcblk0 status=progress
```

This can take some time.

## Hardware Setup

This section covers all the physical bits that need to be plugged in together to give you something to use.  Note when handling the raspberry pi, hold it lightly by the edges to avoid damaging the electronics.

1. Now that the OS has been installed on the SD card, plug the SD card into the raspberry pi.
2. Plug in usb keyboard and mouse.
3. Plug in your monitor via HDMI cable.
4. Once all the above is plugged in, plug in the micro usb to power it up.

If successful, you should see:

1. A solid red light that indicates it is getting power.
2. A flickering green light indicates that a program is running.

## Logging In


