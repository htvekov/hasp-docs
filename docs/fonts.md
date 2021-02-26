<h1>Fonts</h1>

## Built-in Fonts

The ESP8266 firmware only has 1 built-in font: Unscii with font size 8pt.

The ESP32 additionally contains the Ubuntu Condensed font in these font sizes: 12, 16, 22 and 28pt.

The built-in fonts can be set by using the pointsize as parameter:

for example:
```
p4b1.text_font=16
p4b2.value_font=8
```

## Built-in Icons

These icons are included in the built-in font sizes:

{{ read_csv("docs/assets/csv/icons.csv") }}

To use an icon in a text you need to prefix the UTF-8 value with `\u`.
To ensure proper decoding the payload should be used with a `json` or `jsonl` command.

`jsonl` example:
```
{"obj":"label","id":10,"x":0,"y":0,"w":70,"h":50,"parentid":5,"text":"\uf00c OK"}
```

`json` example:
```
["p2b10.text=\uf00c OK"]
```

## Custom Fonts

You can add a custom font by uploading it to the internal flash.
Apply it as the default font on the Configuration > HASP Settings page.

## FontAwesome Icons

