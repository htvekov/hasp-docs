
<h1>Styling Properties</h1>

You can adjust the appearance of objects by changing the foreground, background and/or border color of each object.
Some objects allow for more complex syling, effectively changing its appearance or its sub-components.



### Padding and Margin

Padding sets the space on the inner sides of the edges. It means "I don't want my children too close to my sides, so keep this space". Padding inner sets the "gap" between the children. Margin sets the space on the outer side of the edges. It means "I want this space around me".

Objects use them to set spacing. See the documentation of the objects for the details.

| Property      | Type| Required | Default | Description
|---------------|-----|----------|---------|--------------
| pad_top       | int | | | Set the padding on the top
| pad_bottom    | int | | | Set the padding on the bottom
| pad_left      | int | | | Set the padding on the left
| pad_right     | int | | | Set the padding on the right
| pad_inner     | int | | | Set the padding inside the object between children
| margin_top    | int | | | Set the margin on the top
| margin_bottom | int | | | Set the margin on the bottom
| margin_left   | int | | | Set the margin on the left
| margin_right  | int | | | Set the margin on the right

### Background

The color and gradient used for drawing the background of an object.

| Property       | Type   | Required | Default | Description
|----------------|--------|----------|---------|--------------
| bg_opa         | byte   | no       | ""      | The background opacity level
| bg_color       | color  | no       | true    | The background color
| bg_grad_color  | color  | no       | 0       | The background gradient color
| bg_grad_dir    | [0..2] | no       | expand  | 0 = None, 1 = Horizontal, 2 = Vertical
| bg_grad_stop   | byte   | no       | expand  | Specifies where the gradient should stop. 0: at left/top most position, 255: at right/bottom most position. Default value: 255.
| bg_main_stop   | byte   | no       | expand  | Specifies where should the gradient start. 0: at left/top most position, 255: at right/bottom most position. Default value: 0.

To adjust the background style of a page use `p[x].b[0]` where `x` is the page number.


### Border

The border is drawn on top of the background. It has radius rounding.

| Property     | Type  | Required | Default | Description
|--------------|-------|----------|---------|--------------
| border_color | color | | | Specifies the color of the border
| border_opa   | byte  | | | Specifies opacity of the border
| border_width | byte  | | | Set the width of the border
| border_side  | byte  | | | Specifies which sides of the border to draw. Can be 0=LV_BORDER_SIDE_NONE/1=LEFT/2=RIGHT/4=TOP/8=BOTTOM/15=FULL. A sum of these values is also possible to select specific sides.
| border_post  | bool  | | | If `true` the border will be drawn after all children have been drawn.

### Shadow

The shadow is a blurred area under the object.

| Property | Type       | Required | Default | Description
|----------|------------|----------|---------|--------------
| shadow_color | color  | | | Specifies the color of the shadow
| shadow_opa   | byte   | | | Specifies opacity of the shadow
| shadow_width | int16  | | | Set the width (blur size) of the outline
| shadow_ofs_x | int16  | | | Set the an X offset for the shadow
| shadow_ofs_y | int16  | | | Set the an Y offset for the shadow
| shadow_spread | byte  | | | make the shadow larger than the background in every direction by this value

### Value

Value is an arbitrary text drawn on top of an object. It can be a lightweight replacement for creating label objects.

| Property           | Type   | Required | Default | Description
|--------------------|--------|----------|---------|--------------
| value_str          | string | | | Text to display. Only the pointer is saved! (Don't use local variable with lv_style_set_value_str, instead use static, global or dynamically allocated data)
| value_color        | color  | | | Color of the text
| value_opa          | byte   | | | Opacity level of the text [0-255]
| value_font         | byte   | | | The [Font ID](fonts.md)
| value_letter_space | int    | | | Letter space of the text
| value_line_space   | int    | | | Line space of the text
| value_align        | align  | | | Alignment of the text. Can be LV_ALIGN_.... Default value: LV_ALIGN_CENTER.
| value_ofs_x        | int    | | | X offset from the original position of the alignment
| value_ofs_y        | int    | | | Y offset from the original position of the alignment

### Text

Properties for textual object.

| Property          | Type | Required | Default | Description
|-------------------|------|----------|---------|--------------
| text_color        | color| | | Color of the text
| text_opa          | byte | | | Opacity level of the text [0-255]
| text_font         | byte | | | The [Font ID](fonts.md)
| text_letter_space | int  | | | Letter space of the text
| text_line_space   | int  | | | Line space of the text
| text_decor        | byte | | | Add text decoration. 0=None, 1=Underline, 2=Strikethrough, 3=Underline&Strikethrough
| text_sel_color    | color| | | Set background color of text selection

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