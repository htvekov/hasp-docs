
<h1>Dash UI</h1>

## Code

`pages.jsonl` file:

```json
{"page":1,"comment":"---------- Page 1 ----------"}
{"id":0,"bg_color":"#FFFFFF","text_color":"#000000","radius":0,"border_side":0}
{"obj":"btn","id":1,"x":0,"y":0,"w":240,"h":30,"text":"LIVING ROOM","value_font":22,"bg_color":"#2C3E50","text_color":"#FFFFFF","radius":0,"border_side":0}
{"obj":"arc","id":2,"x":5,"y":45,"w":140,"h":100,"max":40,"border_side":0,"type":0,"rotation":0,"start_angle":180,"end_angle":0,"start_angle1":180,"value_font":12,"value_ofs_x":-19,"value_ofs_y":-4,"bg_opa":0}
{"obj":"arc","id":3,"x":130,"y":45,"w":140,"h":100,"max":100,"border_side":0,"type":0,"start_angle":180,"end_angle":0,"start_angle1":180,"value_font":12,"value_color":"#000000","value_ofs_x":-19,"value_ofs_y":-4,"bg_opa":0}
{"obj":"btn","id":4,"x":0,"y":120,"w":240,"h":20,"val":0,"text":"CO2 levels: ","radius":0,"border_side":0}
{"obj":"label","id":5,"x":2,"y":35,"w":140,"text":"Temperature"}
{"obj":"label","id":6,"x":140,"y":35,"w":140,"text":"Humidity"}
{"obj":"btn","id":7,"x":0,"y":160,"w":240,"h":20,"text":"LIGHTS","bg_color":"#F1C40F","text_color":"#FFFFFF","radius":0,"border_side":0}
{"obj":"label","id":8,"x":20,"y":190,"w":140,"h":20,"text":"Ceiling Light"}
{"obj":"switch","id":9,"x":160,"y":190,"w":40,"h":20,"toggle":"TRUE"}
{"obj":"label","id":10,"x":20,"y":215,"w":140,"h":20,"text":"Wall Light"}
{"obj":"switch","id":11,"x":160,"y":215,"w":40,"h":20,"toggle":"TRUE"}
{"obj":"label","id":12,"x":20,"y":240,"w":200,"h":20,"text":"Ambient Light"}
{"obj":"slider","id":13,"x":30,"y":265,"w":200,"h":10}

{"page":0,"comment":"---------- All pages ----------"}
{"page":0,"obj":"btn","id":1,"x":0,"y":290,"w":76,"h":30,"opacity":50,"text":"\uF053","radius":0,"bg_color":"#34495E","text_color":"#000000"}
{"page":0,"obj":"btn","id":2,"x":75,"y":290,"w":90,"h":30,"opacity":100,"text":"\uF015","radius":0,"bg_color":"#34495E","text_color":"#000000"}
{"page":0,"obj":"btn","id":3,"x":164,"y":290,"w":76,"h":30,"opacity":100,"text":"\uF054","radius":0,"bg_color":"#34495E","text_color":"#000000"}
```
## Result

Values for Temperature, Humidity and CO2 Sensor are sent from another device by publishing to the appropriate command topic:

- hasp/lanbon/command/p1b2.val %value% - update Temperature arc value
- hasp/lanbon/command/p1b2.value_str %value%°C - update Temperature text value
- hasp/lanbon/command/p1b3.val %value% - update Humidity arc value 
- hasp/lanbon/command/p1b3.value_str %value% %  - update Humidity text value
- hasp/lanbon/command/p1b4.text CO2 levels: %value% - update CO2 level value

![Screenshot](assets/images/screenshots/lanbon.png){: align=left }

<div style="clear:both;"></div>
