CC=avr-gcc
CFLAGS=-I. -I/usr/avr/include/ -Wall -Os
MCU=atmega8
PROGRAMMATOR=avrispmkII
PROGRAMMATOR_INTERFACE=usb

all: compile flash

compile:
	$(CC) -mmcu=$(MCU) $(CFLAGS) -o build/main.elf main.c
	avr-objcopy -j .text -O ihex build/main.elf build/main.hex

flash: build/main.elf build/main.hex
	avrdude -p $(MCU) -c $(PROGRAMMATOR) -U flash:w:main.hex:i -F -P $(PROGRAMMATOR_INTERFACE)

size: build/main.elf
	avr-size -C build/main.elf

clean:
	rm -f *.elf *.hex
