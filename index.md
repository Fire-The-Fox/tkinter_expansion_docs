# Get started

## Info 

Tkinter expansion is python library that expands tkinter with bunch of cool stuff.

## Contains

| Feature     | Implemented       |
| ----------- | ------------------|
| Designer    | :white_check_mark:|
| Themes      | :white_check_mark:|
| Hints       | :white_check_mark:|
| RGB color   | :white_check_mark:|
| Xml wrapper | :x: Security issue|
| Css wrapper | :x: Working on    |

tree structure of tkinter_expansion:
```
tkinter_expansion
├─ Classes
│  ├─ Designer
│  │  └─ Methods
│  │     ├─ select_widget
│  │     ├─ un_select 
│  │     ├─ save
│  │     ├─ load
│  │     └─ set_theme_name - argument: theme_name
│  └─ DesignerThemeNotFound
└─ Methods
   ├─ bind_help - armugents: tkinter widget, help_text
   ├─ unbind_help - argument: tkinter widget
   ├─ rgb_to_hex - arguments: red, geen, blue
   └─ hex_to_rgb - argmuent: hex color

```
## Installation

### From pip

```
pip install tkinter_expansion
```

### From source

```
git clone https://github.com/Fire-The-Fox/tkinter_expansion.git
cd tkinter_expansion
python setup.py install
```

## Examples

### Creating gui with Designer without themes

``` py
import tkinter as tk
import tkinter_expansion as tke

# App base

root = tk.Tk()
root.configure(width=700, height=700)

# Initializing Designer

# make sure you have set share_locals and share_globals!
designer = tke.Designer(master=root, share_locals=locals(), share_globals=globals())

# App widgets
window = tk.Button(root)
window.place(relx=0, rely=0, relheight=1, relwidth=1)

# Designer.show is set True by default.
# When you are done with designing just put show=False in tke.Designer()

if designer.show:
    window.bind("<Button-3>", lambda event: designer.select_widget(event))
    window.bind_all("<Escape>", lambda event: designer.un_select())

root.mainloop()
```

### Creating gui with Designer and with theme created.

``` py
import tkinter as tk
import tkinter_expansion as tke

# App base

root = tk.Tk()
root.configure(width=700, height=700)

# Initializing Designer

# make sure you have set share_locals and share_globals!
designer = tke.Designer(master=root, share_locals=locals(), share_globals=globals())
designer.set_theme_name("theme_name") # or blank for default
theme_data = designer.load()

# App widgets

window = tk.Button(root, bg=theme_data["window"]["background"],
                   activeforeground=theme_data["window"]["activeforeground"],
                   activebackground=theme_data["window"]["activebackground"],
                   highlightcolor=theme_data["window"]["highlightcolor"],
                   highlightbackground=theme_data["window"]["highlightbackground"])
window.place(relx=0, rely=0, relheight=1, relwidth=1)

# Designer.show is set True by default.
# When you are done with designing just put show=False in tke.Designer()

if designer.show:
    window.bind("<Button-3>", lambda event: designer.select_widget(event))
    window.bind_all("<Escape>", lambda event: designer.un_select())

root.mainloop()
```

### Converting rgb color to hex

```
import tkinter as tk
import tkinter_expansion as tke

[ code ]
window = tk.Button(root, bg=tke.rgb_to_hex(255, 7, 77))
window.place(relx=0, rely=0, relheight=1, relwidth=1)
[ code ]
```

### Creating fully working hints
```
import tkitner_expansion as tke

root = tk.Tk()

widget = tk.Label(root)
widget.place(x=0, y=0, relwidth=1, relheight=1)
tke.bind_help(widget, "I am hint")
tke.unbind_help(widget)
root.mainloop()
```