# Intel Galileo


The Intel Galileo board is the first "Arduino Certified" board, it differs from a regular Arduino because the Intel Galileo uses a Intel Quark System On a Chip, 32 bit with 256 MB of RAM. The Intel Galileo has Arduino headers so you can plug in and continue with your Arduino projects. In addition, the Intel Galileo has an Ethernet port, a 3.5mm jack, USB client to connect the Galileo to a PC for uploading code, and a USB host for peripherals, even Mini PCI Express on the back of the board.

Galileo runs Linux by default burned in the ROM of the board, but it can boot from a mini SD card if you want another version of Linux.


![](https://cdn.sparkfun.com/assets/f/0/3/2/5/52e14c29ce395f7d3b8b4567.png)


To upload code and use our Intel Galileo we just need to plug in the USB client to our computer and with Arduino do a sketch and compile it, this process will compile the code and transfer it to our board. For more examples on how to create sketches please visit the [Arduino Installation Page](https://software.intel.com/en-us/get-started-arduino-install).


To use the terminal, we have to plug in a 3.5 mm cable into the 3.5 mm jack port, to DB9 and DB9 to USB. Most operating systems will not recognize the board if is just connected through DB9; therefore, a DB9 to USB cable is needed.



Galileo is a microcontroller board based on the Intel® Quark SoC X1000 Application Processor, a 32-bit Intel Pentium-class system on a chip (datasheet). It’s the first board based on Intel® architecture designed to be hardware and software pin-compatible with Arduino shields designed for the Uno R3. Digital pins 0 to 13 (and the adjacent AREF and GND pins), Analog inputs 0 to 5, the power header, ICSP header, and the UART port pins (0 and 1), are all in the same locations as on the Arduino Uno R3. This is also known as the Arduino 1.0 pinout.

Galileo is designed to support shields that operate at either 3.3V or 5V. The core operating voltage of Galileo is 3.3V. However, a jumper on the board enables voltage translation to 5V at the I/O pins. This provides support for 5V Uno shields and is the default behavior. By switching the jumper position, the voltage translation can be disabled to provide 3.3V operation at the I/O pins.