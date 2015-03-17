This instructions were tested on Raspbian.

Unless you have done any distro with libusb-1.0 on the Raspberry Pi, the following instructions should works fine on your raspberry distro.

# Dependencies #
First, install the packages available on Raspbian.
```
> apt-get install python-imaging python-serial python-setuptools
```

## PyUSB ##
PyUSB 1.0 is not available on Ubuntu, so you have to download and install it manually

  1. Download the latest tarball from [Sourceforge](http://sourceforge.net/projects/pyusb/files/)
  1. Decompress the zip file
  1. Install the library
```
> wget ...
> unzip pyusb*.zip
> cd pyusb*
> python setup.py build
> sudo python setup.py install
```

## python-qrcode ##
  1. Checkout the code from github
  1. Install the library
```
> git clone https://github.com/lincolnloop/python-qrcode
> cd python-qrcode
> python setup.py build
> sudo python setup.py install
```

# Installation #
## escpos 1.0-1 ##
If you have installed pyusb for libusb-1.0 then you need to:
  1. Download the latest file
  1. Decompress the file
  1. Install the library
```
> wget http://python-escpos.googlecode.com/files/python-escpos-1.0.tgz
> tar zxvf python-escpos-1.0.tgz
> cd python-escpos-1.0
> python setup.py build
> sudo python setup.py install
```

## Legacy escpos ##
If you want to keep safe with the distro packages and/or you prefer to use libusb-0.1, then you can use the legacy zip file (the one without the "1.0" at the end) and do as root:
```
> cd /usr/local/lib/python2.7/dist-packages/
> wget http://python-escpos.googlecode.com/files/python-escpos.tgz 
> tar zxvf python-escpos.tgz
> rm python-escpos.tgz
> mv python-escpos escpos
> apt-get install python-imaging python-usb python2.7-usbtc08 python-serial
> echo 'SUBSYSTEM=="usb", ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0202", MODE="0664", GROUP="dialout"' > /etc/udev/rules.d/99-escpos.rules
> service udev restart
```
Now you can attach your printer and and test it with the example code in the README file.