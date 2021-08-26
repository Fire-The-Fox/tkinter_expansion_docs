# Designer.save()

## Info

`Designer.save()` method creates folder named "themes" and if you haven't set theme name with `Designer.set_theme_name("theme_name")` theme is going to be named default.

Because themes are stored in .json you can easily create your own themes without using designer.

## Usage

There is no usage because it's private method

## Problem with bigger applications

when application have too many widgets and they have custom theme, reading and changing something will take some time. So when you are finished just redesign theme from:

```
{"window": {"activeforeground": "#ff074d", "activebackground": "#ff074d", "background": "#ff074d", "highlightcolor": "#ff074d", "highlightbackground": "#ff074d"}}
```

to: 

```
{"window": 
	{"activeforeground": "#ff074d",
	 "activebackground": "#ff074d", 
	 "background": "#ff074d",
	 "highlightcolor": "#ff074d",
	 "highlightbackground": "#ff074d"
	}
}
```

And if you are lazy then just don't do that. Or just don't worry too much because linux desktop enviroment themes are more complex than this 🙂

