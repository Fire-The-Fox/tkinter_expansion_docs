# tkinter_expansion.rgb_to_hex()

## Info

Sometimes when you want to make color fade effect on widget it's going to be harder to do with hex color
so `tkinter_expansion.rgb_to_hex()` is about creating hex color based on rgb values

`tkinter_expansion.rgb_to_hex()` requires 3 arguments:

red: value from 0 to 255<br>
green: value from 0 to 255<br>
blue: value from 0 to 255<br>

returns hex value from rgb color

## Usage

```
import tkinter_expansion as tke

color = tke.rgb_to_hex(255, 7, 77)

print(color)
```
output:
```
#ff074d
```