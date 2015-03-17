# Escpos class #

Escpos inherits its methods to the printers.  the following methods are defined:

### image("image\_name.ext") ###
Prints an image. Its adjust the size in order to print it.

  * **image\_name.ext** is the complete file name and location of any image type (jpg, gif, png, bmp)

Raises _ImageSizeError_ exception.

### qr("text") ###
Prints a QR code. The size has been adjuested to Version 4, so it can be enough small to be printed but also enough big to be read by a smartphone.

  * **text** Any text that needs to be QR encoded. It could be a slogan, salutation, url, etc.

### barcode("code", "barcode\_type", width, height, "position", "font") ###
Prints a barcode.
  * **code** is an alphanumeric code to be printed as bar code
  * **barcode\_type** must be one of the following type of codes:
    * UPC-A
    * UPC-E
    * EAN13
    * EAN8
    * CODE39
    * ITF
    * NW7
  * **width** is a numeric value in the range between (1,255) _Default:_ 64
  * **height** is a numeric value in the range between (2,6) _Default:_ 3
  * **position** is where to place the code around the bars, could be one of the following values:
    * ABOVE
    * BELOW
    * BOTH
    * OFF
> _Default:_ BELOW
  * **font** is one of the 2 type of fonts, values could be:
    * A
    * B
> _Default:_ A
Raises _BarcodeTypeError_, _BarcodeSizeError_, _BarcodeCodeError_ exceptions.

### text("text") ###
Prints raw text.
Raises _TextError_ exception.

### set("align", "font", "type", width, height) ###
Set text properties.
  * **align** set horizontal position for text, the possible values are:
    * CENTER
    * LEFT
    * RIGHT
> > _Default:_ left
  * **font** type could be `A` or `B`. _Default:_ A
  * **type** type could be `B` (Bold), `U` (Underline) or `normal`. _Default:_ normal
  * **width** is a numeric value, 1 is for regular size, and 2 is twice the standard size. _Default_: 1
  * **height** is a numeric value, 1 is for regular size and 2 is twice the standard size. _Default_: 1

### cut("mode") ###
Cut paper.
  * **mode** set a full or partial cut. _Default:_ full

> Partial cut is not implemented in all printers.

### cashdraw(pin) ###
Sends a pulse to the cash drawer in the specified pin.
  * **pin** is a numeric value which defines the pin to be used to send the pulse, it could be 2 or 5.
Raises _CashDrawerError()_

### hw("operation") ###
Hardware operations.
  * **operation** is any of the following options:
    * INIT
    * SELECT
    * RESET

### control("align") ###
Carrier feed and tabs.
  * **align** is a string which takes any of the following values:
    * LF _for Line Feed_
    * FF _for Form Feed_
    * CR _for Carriage Return_
    * HT _for Horizontal Tab_
    * VT _for Vertical Tab_