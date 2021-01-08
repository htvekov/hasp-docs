
<h1>Styling Properties</h1>

You can adjust the appearance of objects by changing the foreground, background and/or border color of each object.
Some objects allow for more complex syling, effectively changing its appearance or its sub-components.



### Padding and Margin

Padding sets the space on the inner sides of the edges. It means "I don't want my children too close to my sides, so keep this space". Padding inner sets the "gap" between the children. Margin sets the space on the outer side of the edges. It means "I want this space around me".

Objects use them to set spacing. See the documentation of the [objects](objects.md) for the details.

| Property      | Type | Description | Default |
|---------------|:---: | :--- | :---: |
| pad_top       | int | Set the padding on the top | 0   
| pad_bottom    | int | Set the padding on the bottom | 0   
| pad_left      | int | Set the padding on the left | 0   
| pad_right     | int | Set the padding on the right | 0   
| pad_inner     | int | Set the padding inside the object between children | 0   
| margin_top    | int | Set the margin on the top | 0   
| margin_bottom | int | Set the margin on the bottom | 0   
| margin_left   | int | Set the margin on the left | 0   
| margin_right  | int | Set the margin on the right | 0   

### Background

The color and gradient used for drawing the background of an object.

| Property       | Type   | Req. | Description | Default
|----------------| :---:  |   :---:  |---------| :---:
| bg_opa         | byte   | no       | The background opacity level
| bg_color       | color  | no       | The background color | 
| bg_grad_color  | color  | no       | The background gradient color | 
| bg_grad_dir    | [0..2] | no       | 0 = none<br>1 = horizontal<br>2 = vertical | 0
| bg_grad_stop   | byte   | no       | Specifies where the gradient should stop.<br>0 = at left/top most position<br>255= at right/bottom most position | 255
| bg_main_stop   | byte   | no       | Specifies where should the gradient start<br>0 = at left/top most position<br>255= at right/bottom most position | 0

To adjust the background style of a page use `p[x].b[0]` where `x` is the page number.

### Border

The border is drawn on top of the background. It has radius rounding.

| Property     | Type  | Description
|--------------| :---: |--------------
| border_color | color | Specifies the color of the border
| border_opa   | byte  | Specifies opacity of the border
| border_width | byte  | Set the width of the border
| border_side  | byte  | Specifies which sides of the border to draw.<br>0 = none<br>1 = left<br>2 = right<br>4 = top<br>8 = bottom<br>15 = full<br>A sum of these values is also possible to select specific sides.
| border_post  | bool  | If `true` the border will be drawn after all children have been drawn.

### Shadow

The shadow is a blurred area under the object.

| Property     | Type   | Description
|----------    |  :---: | ----------
| shadow_color | color  | Specifies the color of the shadow
| shadow_opa   | byte   | Specifies opacity of the shadow
| shadow_width | int16  | Set the width (blur size) of the outline
| shadow_ofs_x | int16  | Set the an X offset for the shadow
| shadow_ofs_y | int16  | Set the an Y offset for the shadow
| shadow_spread | byte  | make the shadow larger than the background in every direction by this value

### Value

Value is an arbitrary text drawn on top of an object. It can be a lightweight replacement for creating label objects.

| Property           | Type   | Description   | Default |
| :---               | :---:  | :---          | :---:   |
| value_str          | string | Text to display. Only the pointer is saved! (Don't use local variable with lv_style_set_value_str, instead use static, global or dynamically allocated data)
| value_color        | color  | Color of the text
| value_opa          | byte   | Opacity level of the text [0-255]
| value_font         | byte   | The [Font ID](fonts.md)
| value_letter_space | int    | Letter space of the text
| value_line_space   | int    | Line space of the text
| value_align        | align  | Alignment of the text. Can be: none, left, right, top, bottom, full | center
| value_ofs_x        | int    | X offset from the original position of the alignment
| value_ofs_y        | int    | Y offset from the original position of the alignment

### Text

Properties for textual objects only.

| Property          | Type | Description | Default |
| :---              | :---:  | :---          | :---:   |
| text_color        | color| Color of the text
| text_opa          | byte | Opacity level of the text [0-255]
| text_font         | byte | The [Font ID](fonts.md)
| text_letter_space | int  | Letter space of the text
| text_line_space   | int  | Line space of the text
| text_decor        | byte | Add text decoration.<br>0 = none<br>1 = underline<br>2 = strikethrough<br>3 = underline and strikethrough | 0
| text_sel_color    | color| Set background color of text selection

<!--
### Line

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