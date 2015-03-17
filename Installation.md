# System preparation #
  1. Install [dependencies](https://code.google.com/p/python-escpos/wiki/Dependencies)
  1. Get the _Product ID_ and _Vendor ID_ from the lsusb command
```
 > lsusb
 Bus 002 Device 001: ID 1a2b:1a2b Device name
```
  1. Create a udev rule to let users belonging to _dialout_ group use the printer. You can create the file `/etc/udev/rules.d/99-escpos.rules` and add the following:
```
 SUBSYSTEM=="usb", ATTRS{idVendor}=="1a2b", ATTRS{idProduct}=="1a2b", MODE="0664", GROUP="dialout"
```
> > Replace _idVendor_ and _idProduct_ hex numbers with the ones that you got from the previous step.  Note that you can either, add yourself to "dialout" group, or use another group you already belongs instead "dialout" and set it in the `GROUP` parameter in the above rule.
  1. Restart udev
```
 > sudo service udev restart
```

# Install #

  1. Checkout the code or download the latest compressed file of choice and decompress it
  1. Change directory to python-escpos and install the package
```
 > cd python-escpos
 > python setup.py build
 > sudo python setup.py install
```
  1. Enjoy !!!