# tkinter_expansion.unbind_help()

## Info

With `tkinter_expansion.unbind_help()` you can unbind help from specified widget after their mouse pointer leaves.

required argument:

panel: any tkinter widget

## Usage

```
import tkitner_expansion as tke

root = tk.Tk()

widget = tk.Label(root)
widget.place(x=0, y=0, relwidth=1, relheight=1)
tke.bind_help(widget, "this is help message")
tke.unbind_help(widget)
root.mainloop()
```