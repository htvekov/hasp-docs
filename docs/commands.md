<h1>Commands</h1>

Commands are not related to an object on the screen but can get or set global properties or invoke system commands on the device.

Commands can be issued via the Serial Commandline, Telnet Commandline or MQTT.

For MQTT, use the `hasp/<hostname>/command` topic with payload `<keyword> <parameter(s)>`

Here is a list of all the recognized command keywords:

## Pages

`page`     
value: `[0-12]`, `prev` or `next`

Switches the display to show the objects from a different page and return the page number in `state/page`.

Calling the `page` command without a parameter will return the value of the current page in `state/page`.

`clearpage`     
value: `[0-12]` or `all`

Deletes all objects on a given page. If no page number is specified, it clears the current page.
Use `clearpage all` to clear all objects on all pages.

To delete individual objects, you can issue the `pxby.delete` command.

## Backlight

`dim`   
values: `[0-100]`

Sets the level of the backlight from 0 to 100%, where 0% is off and 100% is full brightness.

!!! example "Example"
    `dim 50` sets the display to half the brightness.

!!! note "Tip"
    This can be used in conjunction with the [idle events][4], e.g. to turn the backlight off after a long period of inactivity.

`light`     
values: `on`/`off`, `true`/`false`, `0`/`1`, `yes`/`no`

Switches the backlight on or off, independent of the set dim level. Turning the backlight on will restore the brightness to the previous dim level.

!!! example "Example"
    `light on` Turn the backlight on 

!!! note "<i class='fa fa-info-circle'></i>&nbsp; Note"
    `dim` and `light` commands will work only if a Backlight GPIO pin is configured to the pin required to control the display backlight.

!!! note "<i class='fa fa-info-circle'></i>&nbsp; Note"
    `dim 0` and `light 0` both turn off the screen, however, with `dim 0` the touching will haven an effect on the objects beneath but not wake the screen, while with `light 0` it will only wake the scren but will not affect the objects.


`wakeup`

Clears the idle state of the device and publishes a `state/idle = OFF` status message.

It resets the idle counter as if a touch event occurred on the device. This is helpful e.g. when you want to wake up the display when an external event has occurred, like a PIR motion sensor.

### Moodlight

An RGB moodlight can be controlled by configuring 3 [GPIO pins][3] as type `Mood Red`, `Mood Green` and `Mood blue`.
These leds can then be controlled together using the `moodlight`command:

```json
moodlight {"state":"off","color":"green"}
moodlight {"state":true,"color":"#ff00e7"}
moodlight {"color":12345}
moodlight {"state":"on","r":255,"g":0,"b":255}
```

- The `power`key accepts [boolean values][2] to turn the moodlight on or off
- The `color` key accepts [color values][1] to set the RGB channels at once
- Individual `r`, `g` and `b` keys can also be used to set each channel seperately

Calling the `moodlight`command without parameters returns the current state:

```json
    "hasp/<platename>/state/moodlight" => {
        "power":"on",
        "color":"#dea1de",
        "r":222,
        "g":161,
        "b":222
    }
```

The color is returned both as hex-value and individual channels.

## System Commands

`calibrate`

Start on-screen touch calibration.

You need to issue a soft reboot command to save the new calibration settings. If you do a hard reset of the device, the calibration settings will be lost.

`screenshot`

Saves a picture of the current screen to the flash filesystem. You can retrieve it via http://&lt;ip-address&gt;/screenshot.bmp.
This can be handy for bug reporting or documentation.

The previous screenshot is overwritten.

`statusupdate`

Reports the status of the MCU. The response will be posted to the state topic:

```json
    "hasp/<platename>/state/statusupdate" => {
        "node":"plate35",
        "status":"available",
        "version":"0.3.3",
        "uptime":1813,
        "ssid":"network",
        "rssi":-63,
        "ip":"192.168.4.2",
        "heapFree":125820,
        "heapFrag":35,
        "espCore":"v3.2.3-14-gd3e562907",
        "espCanUpdate":"false",
        "page":1,
        "numPages":12,
        "tftDriver":"ILI9341",
        "tftWidth":240,
        "tftHeight":320
    }
```

`reboot` or `restart`

Saves any changes in the configuration file and reboots the device.

`update`

value: [url]

Update the firmware from the url provided. Reboots when update was successful.

`factoryreset`

Clear the filesystem and EEPROM and reboot the device in its initial state.

!!! danger "Warning"
    There is no confirmation prompt nor an undo function!

## Output Commands (GPIO)

`output<x>` where `<x>` is number of the group

values: `1` or `0`, `on` or `off`, `true` or `false`

Sets **all** GPIO's assigned to the group number &lt;x> in **Configuration -> [GPIO Configuration][3]** to "0" or "1".

GUI objects that are assigned to the same group using `groupid` during object creation will change state accordingly.

## Configuration Settings

### Wi-FI

`ssid`

Set network name of the access point to connect to.

`pass`

Set the optional password for the access point to connect to.

### MQTT

`hostname`

Set the hostname of the device and mqtt topic for the node to `hasp/<hostname>/`

`mqtthost`

Set the IP address or hostname of the mqtt broker.

`mqttport`

Set the port of the mqtt broker.

`mqttuser`

Set the optional username for the mqtt broker.

`mqttpass`

Set the optional password for the mqtt broker.

### Config/submodule

You can get or set the configuration of a hasp-lvgl submodule in json format.
To get the configuration, use the command `config/<submodule>`. 
The result will be published to `hasp/<hostname>/state/config`. Passwords will be omitted from the result.

```
config/wifi
config/mqtt
config/http
config/mdns
config/hasp {"startdim":100}
config/gui
config/debug {"tele":300}
```

To update the configuration simply issue the same command `config/<submodule>` with updated json payload.

## Multiple Commands

`json`

When you want to execute multiple commands in one payload, you can use the `json` command to create an array of commands in a json payload

Each command is an element in this array of strings:

```json
["page 5","dim 50","light on","statusupdate"]
```

The commands are interpreted and processed sequentially.

`jsonl` (json lines)

This command can be used to create new objects *or* update the properties of an existing object.
When updating an existing object `objid` is not required and will be ignored.

Each line in the `jsonl` payload defines one object and has to be in the json format.

*For details see [Pages](pages.md) and [Objects](objects.md)*

[1]: styling.md#colors
[2]: styling.md#boolean
[3]: configuration/gpio.md
[4]: configuration/display.md#short-idle
