<h1>ESP32-Touchdown</h1>

![Display image](https://cdn.tindiemedia.com/images/resize/Q1ijRaGtVaTcsqY6KOYGnrOphyk=/p/fit-in/994x664/filters:fill(fff)/i/556911/products/2021-01-26T17%3A10%3A19.349Z-osh.JPG?1611652238)

Features:

   - ESP32-WROOM-32D
   - ILI9488 3.5" (480*320) TFT screen in 4-wire SPI mode
   - FT62x6 Capacitive Touch Controller
   - APK2112 3.3V regulator
   - MCP73831 battery management IC
   - CP2102 USB-to-UART IC
   - USB-C connector
   - Piezo Speaker
   - microSD card holder
   - Battery voltage divider connected to GPIO35
   - Stemma / JST-PH I2C connector
   - Compact size: 100x57x15mm

## Video

![YOUTUBE](sdVtHU2Gz7Y)

## Backlight Control

To enable backlight control, you need to solder the jumper pad from position 3-2 to position 2-1:
![Backlight Control](https://camo.githubusercontent.com/82f47f28203f74d19dec720529c5c40368ba7b5c6c29a70e18d1a83d58ec2db0/687474703a2f2f7777772e64757374696e77617474732e6e6c2f45535033322d546f756368446f776e2f6261636b6c696768745f73656c6563742e706e67)

## 3D Printed Cases

You can find several different [3D printable cases](https://github.com/DustinWatts/esp32-touchdown/tree/main/Case) in the [ESP32-Touchdown repository](https://github.com/DustinWatts/esp32-touchdown/):

## Flashing

The ESP32-Touchdown can easily be flashed over USB like any ESP32 development board.

## GPIO Settings

These pins can be used freely as GPIOs:

## PCB Blueprint

The ESP32-Touchdown is fully [Open Source Hardware](https://github.com/DustinWatts/esp32-touchdown/tree/main/Hardware):

- Schematics
- Bill of materials
- PCB layout
- Datasheets

![Display image](https://raw.githubusercontent.com/DustinWatts/esp32-touchdown/main/Hardware/ESP32_TouchDown_dimensions.png)

## LCD Configuration

The `lcd_config.ini` file specifies the different properties of the display, except for the actual pin configuration:

```ini
st7789v =
    -D ST7789_DRIVER=1
    ;-D CGRAM_OFFSET=1         ; Library will add offsets required
    -D TFT_SDA_READ            ; Read from display, it only provides an SDA pin
    -D TFT_WIDTH=240
    -D TFT_HEIGHT=320
    -D TFT_ROTATION=2          ; see TFT_ROTATION values
    ; -D TFT_INVERSION_OFF     ; for normal colors
    ; -D TFT_RGB_ORDER=TFT_RGB   ; Colour order Red-Green-Blue
    -D TFT_RGB_ORDER=TFT_BGR ; Colour order Blue-Green-Red
    -D SPI_FREQUENCY=80000000
    -D SPI_READ_FREQUENCY=6000000 
    -D USER_SETUP_LOADED=1
    -D SUPPORT_TRANSACTIONS
```

## HASP build_flags

Specify the LCD Configuration to use and define the GPIOs in the environment build flags:

```
build_flags =
    ${env.build_flags}
    ${esp32.build_flags}
    ${esp32.vspi}        ; Use VSPI hardware SPI bus

;region -- TFT_eSPI build options ------------------------
    -D USER_SETUP_LOADED=1
    -D ILI9488_DRIVER=1
    -D TFT_ROTATION=0 ; 0=0, 1=90, 2=180 or 3=270 degree
    -D TFT_WIDTH=320
    -D TFT_HEIGHT=480
    -D TFT_CS=15  ;// Chip select control pin
    -D TFT_DC=2  ;// Data Command control pin
    -D TFT_RST=4 ;// Reset pin (could connect to RST pin)
    -D TFT_BCKL=5  ;None, configurable via web UI (e.g. 2 for D4)
    -D SUPPORT_TRANSACTIONS
    -D TOUCH_DRIVER=6336 ; XPT2606 Resistive touch panel driver 
    -D TOUCH_SDA=21
    -D TOUCH_SCL=22
    -D TOUCH_IRQ=27   ; not connected
    -D TOUCH_RST=-1   ; not used, connected to 3.3V
    -D TOUCH_FREQUENCY=400000
    -D SPI_FREQUENCY=27000000
    -D SPI_READ_FREQUENCY=16000000
;endregion
```