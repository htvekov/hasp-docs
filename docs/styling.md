
<h1>Styling Properties</h1>

You can adjust the appearance of objects by changing the foreground, background and/or border color of each object.
Some objects allow for more complex syling, effectively changing its appearance or its sub-components.

### Colors
Color values can be:

- Short names (from table below)
- RGB hex code (`#rrggbb`)
- RGB565 number format (`0..65353`)

<table>
<tr><th style="text-align:center">Hex Code</th><th>Short Name</th><!--th>RGB565 Number</th></tr-->
<tr><td style="background-color:#FFC0CB;text-align:center">#FFC0CB</td><td>Pink</td></tr>
<tr><td style="background-color:#DDA0DD;text-align:center">#DDA0DD</td><td>Plum</td></tr>
<tr><td style="background-color:#DA70D6;text-align:center">#DA70D6</td><td>Orchid</td></tr>
<tr><td style="background-color:#EE82EE;text-align:center">#EE82EE</td><td>Violet</td></tr>
<tr><td style="background-color:#FF00FF;text-align:center;color:white">#FF00FF</td><td>Magenta or Fuchsia</td></tr>
<tr><td style="background-color:#800080;text-align:center;color:white">#800080</td><td>Purple</td></tr>
<tr><td style="background-color:#4B0082;text-align:center;color:white">#4B0082</td><td>Indigo</td></tr>
<tr><td style="background-color:#B00000;text-align:center;color:white">#B00000</td><td>Blush</td></tr>
<tr><td style="background-color:#FF0000;text-align:center;color:white">#FF0000</td><td>Red</td></tr>
<tr><td style="background-color:#FF6347;text-align:center;color:white">#FF6347</td><td>Tomato</td></tr>
<tr><td style="background-color:#FA8072;text-align:center">#FA8072</td><td>Salmon</td></tr>
<tr><td style="background-color:#FF7F50;text-align:center">#FF7F50</td><td>Coral</td></tr>
<tr><td style="background-color:#FFA500;text-align:center">#FFA500</td><td>Orange</td></tr>
<tr><td style="background-color:#FFD700;text-align:center">#FFD700</td><td>Gold</td></tr>
<tr><td style="background-color:#FFFF00;text-align:center">#FFFF00</td><td>Yellow</td></tr>
<tr><td style="background-color:#F0E68C;text-align:center">#F0E68C</td><td>Khaki</td></tr>
<tr><td style="background-color:#FFE4C4;text-align:center">#FFE4C4</td><td>Bisque</td></tr>
<tr><td style="background-color:#F5DEB3;text-align:center">#F5DEB3</td><td>Wheat</td></tr>
<tr><td style="background-color:#D2B48C;text-align:center">#D2B48C</td><td>Tan</td></tr>
<tr><td style="background-color:#00FFFF;text-align:center">#00FFFF</td><td>Cyan or Aqua</td></tr>
<tr><td style="background-color:#00FF00;text-align:center">#00FF00</td><td>Lime</td></tr>
<tr><td style="background-color:#008000;text-align:center;color:white">#008000</td><td>Green</td></tr>
<tr><td style="background-color:#008080;text-align:center;color:white">#008080</td><td>Teal</td></tr>
<tr><td style="background-color:#0000FF;text-align:center;color:white">#0000FF</td><td>Blue</td></tr>
<tr><td style="background-color:#000080;text-align:center;color:white">#000080</td><td>Navy</td></tr>
<tr><td style="background-color:#808000;text-align:center;color:white">#808000</td><td>Olive</td></tr>
<tr><td style="background-color:#CD853F;text-align:center;color:white">#CD853F</td><td>Peru</td></tr>
<tr><td style="background-color:#A0522D;text-align:center;color:white">#A0522D</td><td>Sienna</td></tr>
<tr><td style="background-color:#A52A2A;text-align:center;color:white">#A52A2A</td><td>Brown</td></tr>
<tr><td style="background-color:#800000;text-align:center;color:white">#800000</td><td>Maroon</td></tr>
<tr><td style="background-color:#FFFFFF;text-align:center">#FFFFFF</td><td>White</td></tr>
<tr><td style="background-color:#FFFAFA;text-align:center">#FFFAFA</td><td>Snow</td></tr>
<tr><td style="background-color:#FFFFF0;text-align:center">#FFFFF0</td><td>Ivory</td></tr>
<tr><td style="background-color:#FAF0E6;text-align:center">#FAF0E6</td><td>Linen</td></tr>
<tr><td style="background-color:#F5F5DC;text-align:center">#F5F5DC</td><td>Beige</td></tr>
<tr><td style="background-color:#F0FFFF;text-align:center">#F0FFFF</td><td>Azure</td></tr>
<tr><td style="background-color:#C0C0C0;text-align:center">#C0C0C0</td><td>Silver</td></tr>
<tr><td style="background-color:#808080;text-align:center;color:white">#808080</td><td>Gray or Grey</td></tr>
<tr><td style="background-color:#000000;text-align:center;color:white">#000000</td><td>Black</td></tr>
</table>

#### Setting Color

Examples:
```json
p[0].b[2].value_color=13891
p[1].b[5].text_color=silver
p[2].b[3].bg_color=#C0C0C0
```

#### Return values

When retrieving the color of an object, both the HTML representation as the RGB values are returned seperately.

The format will be a json object with components:

- color : 6 digit hexadecimal code preceeded by a hash `#` sign.
- r : byte value for red (`0..255`)
- g : byte value for green (`0..255`)
- b : byte value for blue (`0..255`)

For example, the color returned by a color picker change event is:
```json
hasp/plate_123/state/p1b4 => {"color":"#00fff6","r":"0","g":"255","b":"246"}
```

### Background

The color and gradient used for drawing the background of an object.

| Property       |   Type   | Description
| :---           |   :---:  | :---
| bg_opa         | byte     | The background opacity level
| bg_color       |[color][1]| The background color
| bg_grad_color  |[color][1]| The background gradient color
| bg_grad_dir    | [0..2]   | 0 = none *(=default)*<br>1 = horizontal<br>2 = vertical
| bg_grad_stop   | byte     | Specifies where the gradient should stop.<br>0 = at left/top most position<br>255= at right/bottom most position *(=default)*
| bg_main_stop   | byte     | Specifies where should the gradient start<br>0 = at left/top most position *(=default)*<br>255= at right/bottom most position

To adjust the background style of a page use `p[x].b[0]` where `x` is the page number.

### Border

The border is drawn on top of the background. It has radius rounding.

| Property     |  Type    | Description
| :---         |  :---:   | :---
| border_color |[color][1]| Specifies the color of the border
| border_opa   | byte     | Specifies opacity of the border
| border_width | byte     | Set the width of the border
| border_side  | byte     | Specifies which sides of the border to draw.<br>0 = none<br>1 = left<br>2 = right<br>4 = top<br>8 = bottom<br>15 = full<br>A sum of these values is also possible to select specific sides.
| border_post  | bool     | If `true` the border will be drawn after all children have been drawn.

### Line

Properties for line objects only.

| Property          |  Type    | Description | Default |
| :---              |  :---:   | :---          | :---:   |
| line_color        |[color][1]| Color of the line
| line_opa          | byte     | Opacity level of the line [0-255]
| line_width        | int      | Width of the line. | 0
| line_dash_width   | int      | Width of dash. Dashing is drawn only for horizontal or vertical lines. `0` = disable dash | 0
| line_dash_gap     | int      | Gap between two dash line. Dashing is drawn only for horizontal or vertical lines. `0` = disable dash| 0
| line_rounded      | bool     | `true` = draw rounded line endings | `false`

### Padding and Margin

Padding sets the space on the inner sides of the edges. It means "I don't want my children too close to my sides, so keep this space". Padding inner sets the "gap" between the children. Margin sets the space on the outer side of the edges. It means "I want this space around me".

Objects use them to set spacing. See the documentation of the [objects](objects.md) for the details.

| Property      | Type | Description | Default |
| :---          |:---: | :--- | :---: |
| pad_top       | int | Set the padding on the top | 0   
| pad_bottom    | int | Set the padding on the bottom | 0   
| pad_left      | int | Set the padding on the left | 0   
| pad_right     | int | Set the padding on the right | 0   
| pad_inner     | int | Set the padding inside the object between children | 0   
| margin_top    | int | Set the margin on the top | 0   
| margin_bottom | int | Set the margin on the bottom | 0   
| margin_left   | int | Set the margin on the left | 0   
| margin_right  | int | Set the margin on the right | 0   

### Shadow

The shadow is a blurred area under the object.

| Property      |  Type    | Description
| :---          |  :---:   | :---
| shadow_color  |[color][1]| Color of the shadow
| shadow_opa    | byte     | Specifies opacity of the shadow
| shadow_width  | int16    | Set the width (blur size) of the outline
| shadow_ofs_x  | int16    | Set the an X offset for the shadow
| shadow_ofs_y  | int16    | Set the an Y offset for the shadow
| shadow_spread | byte     | Make the shadow larger than the background in every direction by this value

### Text

Properties for textual objects only.

| Property          |  Type    | Description
| :---              |  :---:   | :---
| text_color        |[color][1]| Color of the text
| text_opa          | byte     | Opacity level of the text [0-255]
| text_font         | byte     | The [Font ID](fonts.md)
| text_letter_space | int      | Distance between letters of the text, can be a negative number
| text_line_space   | int      | Distance between lines of the text, can be a negative number 
| text_decor        | byte     | Add text decoration.<br>0 = none *(=default)*<br>1 = underline<br>2 = strikethrough<br>3 = underline and strikethrough
| text_sel_color    |[color][1]| Set background color of text selection

### Value

Value is an arbitrary text drawn on top of an object. It can be a lightweight replacement for creating label objects.

| Property           |  Type    | Description
| :---               |  :---:   | :---
| value_str          | string   | Text to display. Only the pointer is saved! (Don't use local variable with lv_style_set_value_str, instead use static, global or dynamically allocated data)
| value_color        |[color][1]| Color of the text
| value_opa          | byte     | Opacity level of the text [0-255]
| value_font         | byte     | The [Font ID](fonts.md)
| value_letter_space | int      | Distance between letters of the text, can be a negative number
| value_line_space   | int      | Distance between lines of the text, can be a negative number
| value_align        | align    | Alignment of the text. Can be: none, left, right, top, bottom, full or center *(=default)*
| value_ofs_x        | int      | X offset from the original position of the alignment
| value_ofs_y        | int      | Y offset from the original position of the alignment

<!--

n/a

### Image

n/a

### Outline

n/a

### Pattern

n/a

### Transitions

n/a

-->

[1]: #colors