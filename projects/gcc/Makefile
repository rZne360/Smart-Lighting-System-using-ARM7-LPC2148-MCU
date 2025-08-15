# Simple Makefile for LPC2148 using arm-none-eabi-gcc (adjust paths as needed)
TARGET = smart_lighting
MCU = arm7tdmi
C_SOURCES = ../src/main.c

CC ?= arm-none-eabi-gcc
OBJCOPY ?= arm-none-eabi-objcopy
OBJDUMP ?= arm-none-eabi-objdump
SIZE ?= arm-none-eabi-size

CFLAGS = -mcpu=$(MCU) -mthumb-interwork -Os -ffunction-sections -fdata-sections -Wall -Wextra
LDFLAGS = -nostartfiles -Wl,--gc-sections

all: $(TARGET).elf $(TARGET).bin

$(TARGET).elf: $(C_SOURCES)
	$(CC) $(CFLAGS) $(LDFLAGS) -o $@ $^
	$(SIZE) $@

$(TARGET).bin: $(TARGET).elf
	$(OBJCOPY) -O binary $< $@

clean:
	rm -f $(TARGET).elf $(TARGET).bin
