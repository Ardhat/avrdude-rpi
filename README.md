Using avrdude with Ardhat
==========================

Since the Raspberry Pi lacks a DTR pin to trigger the Arduino optiboot bootloader during code upload to
Ardhat, we use a modified version of avrdude to emulate a DTR line.  

Instructions:
-------------

Copy both files into your /usr/bin directory, then rename the original avrdude to avrdude-original
and symlink avrdude-autoreset to become avrdude.

    cp autoreset /usr/bin
    cp avrdude-autoreset /usr/bin
    mv /usr/bin/avrdude /usr/bin/avrdude-original
    ln -s /usr/bin/avrdude-autoreset /usr/bin/avrdude


Now when you run avrdude from anywhere (including via Arduino's normal UI) it will flag GPIO13 when
it is about to upload hex data to Ardhat (Ardhat uses GPIO13 to connect to the ATmega reset line) .
