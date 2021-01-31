<h1>Installation</h1>

## Download the firmware

Go to the [releases](https://github.com/fvanroie/hasp-lvgl/releases) page on GitHub to download the latest hasp-lvgl binaries.

Get the files required for ESP32:

- d1-mini-esp32_ili9341_v0.3.2.bin
- bootloader_dio_40m.bin
- boot_app0.bin
- partitions.bin

!!! note
    You can also download the *nightly* hasp-lvgl firmware.zip file from the [Actions tab](https://github.com/fvanroie/hasp-lvgl/actions?query=workflow%3A%22PlatformIO+CI%22) on Github.


## Install the firmware

### Flash ESP32

When flashing the ESP32 for the first time, you need to install a bootloader, partition scheme and application loader:

```shell
esptool.py --port "COM1" erase_flash
esptool.py --port "COM1" write_flash 0x1000 bootloader_dio_40m.bin --flash_mode dio --flash_freq 40m
esptool.py --port "COM1" write_flash 0x8000 partitions.bin
esptool.py --port "COM1" write_flash 0xe000 boot_app0.bin
```

Change `COM1` to the correct port on your computer.

then flash the actual firmware:

```shell
esptool.py -p "COM1" --baud 921600 write_flash 0x10000 d1-mini-esp32_ili9341_<version>.bin
```

or all previous steps in one long command line:

```shell
esptool.py -p "COM1" --baud 921600 --before default_reset --after hard_reset write_flash --flash_mode dio --flash_freq 40m --flash_size detect 0x1000 bootloader_dio_40m.bin 0x8000 partitions.bin 0xe000 boot_app0.bin 0x10000 d1-mini-esp32_ili9341_<version>.bin
```
