# Designer

## Info

With tkinter_expansion's Designer class you can edit Design of you application while running and add custom themes support for it.

Only you have to create theme manager for your app and let Designer do it's job.

More info about methods in class Designer can be found in "Designer methods" category

Every widget have it's own unique id that you can get by typing

## Usage

### Designer without themes

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

If you are done with your design. Click save and then close program and open file "default.json" in themes folder. Then just get values and set them.

### Designer with themes

Do this after you have theme created! So first design theme and then load it!

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

themes/default.json
``` json
{"window": {"activeforeground": "#ff074d", "activebackground": "#ff074d", "background": "#ff074d", "highlightcolor": "#ff074d", "highlightbackground": "#ff074d"}}
```

## Understanding usage

tkinter_expansion.Designer() accepts theese arguments:

title: title of designer window ( requires string ),<br>
show: Do you want to show designer or not ( requires bool ),<br>
share_locals: needed argument for getting variable name ( locals() ),<br>
share_globals: needed argument for getting variable name ( globals() )<br>

```
widget.bind("<Button-3>", lambda event: designer.select_widget(event)) # when you right click on that widget it's going to select it in Designer
```

```
window.bind_all("<Escape>", lambda event: designer.un_select()) # pressing esc will unselect that widget from Designer
```

