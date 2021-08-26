# Designer.load()

## Info

`Designer.load()` method loads theme data from theme.json file

themes are stored in "themes" folder same as where you app is.

load returns json data.

## Problem with bigger applications

If your application takes too long to load. Please check theme file if there isn't something in addition to prevent long loading:

Every widget have it's variable name stored with some data. 

for example: 

themes/default.json
```
{"window": {"activeforeground": "#ff074d", "activebackground": "#ff074d", "background": "#ff074d", "highlightcolor": "#ff074d", "highlightbackground": "#ff074d"}, "some_label": {"background": "lime"}}
```

main.py
```
import tkinter as tk
import tkinter_expansion as tke

# basic tkinter application

root = tk.Tk()
root.configure(width=700, height=700)

# designer

designer = tke.Designer(master=root, share_locals=locals(), share_globals=globals(), show=False)
designer.set_theme_name()
theme_data = designer.load()

window = tk.Button(root, bg=theme_data["window"]["background"],
                   activeforeground=theme_data["window"]["activeforeground"],
                   activebackground=theme_data["window"]["activebackground"],
                   highlightcolor=theme_data["window"]["highlightcolor"],
                   highlightbackground=theme_data["window"]["highlightbackground"])
window.place(relx=0, rely=0, relheight=1, relwidth=1)
if designer.show:
    window.bind("<Button-3>", lambda event: designer.select_widget(event))
    window.bind_all("<Escape>", lambda event: designer.un_select())

root.mainloop()
```

Is there any "some_label" variable? No, then just remove it from `themes/default.json`

## Optimization

If are more widgets in your gui that share some values. Just get that value from another widget 

example:<br>
```
[...]
window1 = tk.Label(root, bg=theme_data["window1"]["background"])
[...]
window2 = tk.Label(root, bg=theme_data["window1"]["background"])
[..]
```