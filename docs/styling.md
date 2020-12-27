
## Styling Properties

You can adjust the appearance of objects by changing the foreground, background and/or border color of each object.

## Object Types

Each object type is an ID that indicates which object type that line represents.
Besides the common properties listed above, each object type can have specific properties.

## Button
**objid:10**

A button can have 3 states. All the following parameters can be appended by a number to change the appearance of that state only:

- 0: Released
- 1: Pressed
- 2: Disabled

Or if the postfix index is ommited, then the default state 0 or Pressed is used.

A button can accept the attributes of the following groups:

- Background
- Border
- Outline
- Shadow
- Value

## Attribute Groups

### Padding and Margin

Padding sets the space on the inner sides of the edges. It means "I don't want my children too close to my sides, so keep this space". Padding inner sets the "gap" between the children. Margin sets the space on the outer side of the edges. It means "I want this space around me".

Objects use them to set spacing. See the documentation of the objects for the details.

| Property | Type      | Required | Default | Description
|----------|------------|----------|---------|--------------
| pad_top | int | Set the padding on the top
| pad_bottom | int | Set the padding on the bottom
| pad_left | int | Set the padding on the left
| pad_right | int | Set the padding on the right
| pad_inner | int | Set the padding inside the object between children
| margin_top | int | Set the margin on the top
| margin_bottom | int | Set the margin on the bottom
| margin_left | int | Set the margin on the left
| margin_right | int | Set the margin on the right

### Background

| Property | Type      | Required | Default | Description
|----------|------------|----------|---------|--------------
| bg_opa   | byte       | no       | ""      | The background opacity level
| bg_color   | color    | no       | true    | The background color
| bg_grad_color | color | no       | 0       | The background gradient color
| bg_grad_dir   | [0..2]| no       | expand  | 0 = None, 1 = Horizontal, 2 = Vertical
| bg_grad_stop   | byte | no       | expand  | Specifies where the gradient should stop. 0: at left/top most position, 255: at right/bottom most position. Default value: 255.
| bg_main_stop   | byte | no       | expand  | Specifies where should the gradient start. 0: at left/top most position, 255: at right/bottom most position. Default value: 0.

### Border

The border is drawn on top of the background. It has radius rounding.

| Property | Type      | Required | Default | Description
|----------|------------|----------|---------|--------------
| border_color | color| Specifies the color of the border
| border_opa   | byte | Specifies opacity of the border
| border_width | byte | Set the width of the border
| border_side  | byte | Specifies which sides of the border to draw. Can be 0=LV_BORDER_SIDE_NONE/1=LEFT/2=RIGHT/4=TOP/8=BOTTOM/15=FULL. A sum of these values is also possible to select specific sides.
| border_post  | bool | If `true` the border will be drawn after all children have been drawn.

### Shadow

The shadow is a blurred area under the object.

| Property | Type      | Required | Default | Description
|----------|------------|----------|---------|--------------
| shadow_color | color  | Specifies the color of the shadow
| shadow_opa   | byte   | Specifies opacity of the shadow
| shadow_width | int16  | Set the width (blur size) of the outline
| shadow_ofs_x | int16  | Set the an X offset for the shadow
| shadow_ofs_y | int16  | Set the an Y offset for the shadow
| shadow_spread | byte  | make the shadow larger than the background in every direction by this value

### Value

Value is an arbitrary text drawn to the background. It can be a lightweight replacement for creating label objects.

| Property | Type      | Required | Default | Description
|----------|------------|----------|---------|--------------
| value_str | string | Text to display. Only the pointer is saved! (Don't use local variable with lv_style_set_value_str, instead use static, global or dynamically allocated data)
| value_color | color | Color of the text
| value_opa | byte | Opacity level of the text [0-255]
| value_font | byte | The font ID
| value_letter_space | int | Letter space of the text
| value_line_space | int | Line space of the text
| value_align | align | Alignment of the text. Can be LV_ALIGN_.... Default value: LV_ALIGN_CENTER.
| value_ofs_x | int | X offset from the original position of the alignment
| value_ofs_y | int | Y offset from the original position of the alignment

### Text

Properties for textual object.

| Property | Type      | Required | Default | Description
|----------|------------|----------|---------|--------------
| text_color | color | Color of the text
| text_opa  | byte | Opacity level of the text [0-255]
| text_font | byte | Font ID
| text_letter_space | int | Letter space of the text
| text_line_space | int | Line space of the text
| text_decor | byte | Add text decoration. 0=None, 1=Underline, 2=Strikethrough, 3=Underline&Strikethrough
| text_sel_color | color | Set background color of text selection

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




ected item are send out.