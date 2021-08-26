# tkinter_expansion.bind_help()

## Info

With `tkinter_expansion.bind_help()` you can bind help to specified widget and show after some time

required arguments:

panel: any tkinter widget, <br>
text: help message

## Usage

```
import tkitner_expansion as tke

root = tk.Tk()

widget = tk.Label(root)
widget.place(x=0, y=0, relwidth=1, relheight=1)
tke.bind_help(widget, "this is help message")
root.mainloop()
```