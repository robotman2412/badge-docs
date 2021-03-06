---
title: "Connecting on Mac"
nodateline: true
weight: 10
---
We get it. The fruity aluminum and glass has a certain appeal. However getting a decent serial connection is a bit of work. Not really hard and a nice way to get started with serial hacking on your Mac!
## Preparations
We assume you're running a modern version of Mac OS. First we'll install brew (if you already have it, just skip ahead.
### Brew
Visit [https://brew.sh](https://brew.sh) and use the oneliner you find there to install it. It will take a bit of time but you'll love it!

Brew is the installer every Mac should ship with. A ton of open source apps will become available to you without the hassle. Just type in `brew install $appname` and it will happen!
### Picocom
Install Picocom using `brew install picocom`.

Done. It's that easy.
### Connecting to your badge on Mac
Plug in a USB-Serial board, and maybe install some drivers to get it working. 

On your terminal type `ls /dev/tty.*` and hit enter:

* CP210x chips are usually labeled /dev/tty.SLAB_USBtoUART
* CH340 chips are labeled ...
* FTDI chips are labeled ...
* Prolific 2303 chips should just die. Please discard.

If your USB-Serial doesn't show up in `/dev/tty.*`then the driver hasn't been installed or isn't working properly (or you have a dead USB port or a dead USB-Serial)

Connect the 3.3v and GND to the header on the back of the badge. Connect the RX of the badge to the TX of the USB-Serial, and the TX of the badge to the RX of the USB-Serial. 
### Using Picocom
Picocom is a bit spartan. Start it using 

`picocom --imap delbs -b 115200 /dev/tty.SLAB_USBtoUART`

Instead of `/dev/tty.SLAB_USBtoUART` you should use the device name you found earlier.

When you see a blank screen, press the Enter key twice. A welcoming prompt should be displayed.

Type in `?` and get going in the awesome experience. Type in `a` and verify the symbols you see match the symbols you see on the badge. If you get question marks in blocks, weird symbols etc, your locale is not set right.

Press *control-a* and then *control-h* to see Picocom **help**

Press *control-a* and then *control-x* to **exit** Picocom

### Setting Locale (troubleshooting)
