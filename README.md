# Basic IoT scenario
This is upgraded example based on [Basic IoT scenario lab in Introduction to informatics course](https://wiki.itcollege.ee/index.php/Category:I600_Introduction_to_Computers_and_Informatics#Assignment:_Set_up_basic_IoT_scenario) for TTÜ IT College Cyber Security Engineering first year students.


## Prerequisites
* A WeMos Lolin32 microcontroller with at least one color led
* [pip](https://pip.pypa.io/en/stable/)
* picocom and wget (Linux has them by default. On OS X you need [Homebrew](https://brew.sh/) to install picocom by: ``brew install picocom``)
* [Silabs VCP driver](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers) for OS X
* esptool ``pip install esptool``
* Adafruit-ampy ``pip install adafruit-ampy``

## How to use
### Flashing MicroPython

Install MicroPython:
```
wget http://micropython.org/resources/firmware/esp32-20171017-v1.9.2-279-g090b6b80.bin
esptool.py -p /dev/ttyUSB0 -b 460800 erase_flash
esptool.py -p /dev/ttyUSB0 -b 460800 write_flash --flash_mode dio 0x1000 esp32-*.bin
```

Note that in OS X the ttyUSB0 is replaced with tty.SLAB_USBtoUART. This applies for entire project!
### Get the microcontroller ready

Upload files to ESP32:
```
ampy -p /dev/ttyUSB0 put boot.py
ampy -p /dev/ttyUSB0 put main.py
```

### Run it
Connect through picocom:
```
picocom -b115200 /dev/ttyUSB0
```


Run the code:
```
main()
```

Enter the shown ip into the browser and start blinking.

## Examples
Browser view:

![Pic of browser](http://spruur.eu/dump/iot-led-blink-wifi-img/browser-example.png)

Different led colors:

![Pic of led](http://spruur.eu/dump/iot-led-blink-wifi-img/image1.JPG)

![Pic of led](http://spruur.eu/dump/iot-led-blink-wifi-img/image2.JPG)

![Pic of led](http://spruur.eu/dump/iot-led-blink-wifi-img/image3.JPG)


