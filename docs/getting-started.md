<h1>Getting Started</h1>

hasp-lvgl supports the ESP32, ESP8266 and STM32F4 families of microcontrollers.
It needs a compatible micro-controller with drivers supporting the attached display, touch controller, storage and network.

Below is a list of recommended development boards and a TFT touchscreen to get you up-and-running in no time.

![Plug-and-play](assets/images/lolin-esp.png "ESP with Lolin 2.4&quot;")

## Recommended Boards

<style>
table th:first-of-type {
    width: 12%;
}
table th:nth-of-type(2) {
    width: 22%;
}
table th:nth-of-type(3) {
    width: 22%;
}
table th:nth-of-type(4) {
    width: 22%;
}
table th:last-of-type {
    width: 22%;
}
</style>
|&nbsp;       | Minimal     | Basic        | Standard
|:----        |:----:       |:----:        |:----:
| MCU         | ESP8266     | ESP32-WROOM  | ESP32-WROVER 
| CPU Freq.   | 80Mhz       | 240Mhz       | 240Mhz   
| Ram         | 80Kb        | 520Kb        | 520Kb
| PSRam       | no          | no           | yes
| Minimal Flash | 4MB         | 4MB          | 4MB
| Display     | ILI9341 SPI | ILI9341 SPI  | ILI9341 SPI
| Touch       | XPT2046 SPI | XPT2046 SPI  | XPT2046 SPI
| Network     | Wi-Fi        | Wi-Fi         | Wi-Fi
| Dev. Board* |[D1 mini ESP8266][3]|[D1 mini ESP32][4]|[TTGO T7 v1.5 Mini32][5]
| Firmware    | [Download][1] | [Download][1]  | [Download][1]

[1]: https://github.com/fvanroie/hasp-lvgl/releases
[3]: https://www.aliexpress.com/item/32643142716.html
[4]: https://www.aliexpress.com/item/32815530502.html
[5]: https://www.aliexpress.com/item/32977375539.html

!!! note " "
    *Due to the large number of possible hardware options a selection of 3 popular ESP development boards has been made for the precompiled binaries.*

!!! warning ""
    Advanced users can [build and compile](../compiling) custom configurations using PlatformIO, however this is not currently supported.


## Recommended Display
### Lolin TFT 2.4"

![TFT-LED PWM dimming](assets/images/lolin24tft.png)

ILI9341 SPI touchscreens with backlight dimming via PWM are quite cheap to get.
An ILI9341 TFT display with SPI is required when using a pre-built binary.
The touch controller needs to be the XPT2046 Resistive Touch driver.

The Lolin TFT 2.4" is **plug-and-play** with the 3 recommended ESP development boards.
If you have another ESP or MCU, you can still use this display using jumper cables.
You can also solder a row of headers at the bottom of the display to plug it into a breadboard.
Therefor the Lolin TFT 2.4 Touch Shield is used as the development display of choice.

##### Backlight Control

To use PWM dimming on the Lolin TFT 2.4" you must connect the TFT-LED pin to either D1, D2 or D4.
**D1 is recommended** for backlight control and configured by default.

![TFT-LED PWM dimming](assets/images/tft-led-pwm.png)

!!! danger "<i class="fa fa-exclamation-triangle"></i> Do *not* use D3 for backlight control because it is already in use for touch!"

!!! warning ""
    It is *not* recommended to use D4 for backlight control because it is already in use for PSram on the ESP32-Wrover.
    The D1-mini has D4 connected to on-board LED and boot fails if pulled LOW

### Compatible ESP boards

![TFT-LED PWM dimming](assets/images/esp_boards.png)

The Lolin TFT 2.4" header is **plug-and-play** compatible with these development boards,
no need to use any jumper cables:

**ESP32:**

- Wemos D1 Mini ESP32 *(**only** solder the inner row of pin headers)*
- TTGO T7 V1.5 MINI32 ESP32 *(**only** solder the inner row of pin headers)*
- LOLIN D32 Pro V2.0.0 *using an **additional** TFT cable*

**ESP8266:**

- Wemos D1 Mini ESP8266
- Lolin D1 Mini Pro ESP8266 V2.0.0

!!! note "Note"
    If you have a Lolin TFT 2.4" Display and a compatible ESP development board, you have all the hardware that is needed.
    In that case you can skip ahead to the [Firmware Installation](installation.md).

## Alternative SPI Display

Any common ILI9341 320x240 4-wire SPI touchscreen with XPT2046 Resistive Touch driver can be used, like:

- 2.4" SKU: [MSP2402](http://www.lcdwiki.com/2.4inch_SPI_Module_ILI9341_SKU:MSP2402)
- 2.8" SKU: [MSP2807](http://www.lcdwiki.com/2.8inch_SPI_Module_ILI9341_SKU:MSP2807)
- 3.2" SKU: [MSP3218](http://www.lcdwiki.com/3.2inch_SPI_Module_ILI9341_SKU:MSP3218)

You will need to connect the GPIO pins using jumper wires.
