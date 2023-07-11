---
title: "Æ-Ø-Å"
date: 2023-07-11T11:55:14+02:00
---
## The problem

When using vim editor bindings it is more practical to use the US keyboard layout than a norwegian, due to the easier accessible special characters, characters such as `[{}]"':;\|<>/~`. This is great, once I got out of muscle memory hell.

Although most of the code I write is in english, there is no getting around norwegian on the keyboard. It's become clear that almost every norwegian word I use include these letters. I need access to these.

**But how to get ae-oe-aa to work properly: Æ-Ø-Å... with english keyboard layout in linux**

## The Options
1. Making the norwegian and US keyboards toggleable by a key.
    - pros:
        - Can use the norwegian layout at will
    - cons: 
        - Back to muscle memory hell

2. Making specific keymaps for æ, ø, å and their uppercase siblings Æ, Ø and Å, in the US keyboard.


## The solution


Motivated by this [blogpost](https://blog.stigok.com/2017/07/10/norwegian-keys-on-us-keyboard-layout-with-xmodmap.html) I set out to create some custom keymaps.

I had already used the utility setxkbmap to swap my escape and caps lock key (to avoid serious injury to my left pinky finger in the vim world). However, doing this remap with setxkbmap didn't seem super simple.

What was simple, however, was using the [xmodmap](https://wiki.archlinux.org/title/xmodmap) utility.

`pacman -S xorg-xmodmap`

And add a simple config:
```bash
!# ~/.Xmodmap

! Esc
keycode 9 = Mode_switch ISO_Level3_Shift

! Norwegian characters æÆ øØ åÅ
keycode 47 = semicolon colon oslash Oslash
keycode 48 = apostrophe quotedbl ae AE
keycode 34 = bracketleft braceleft aring Aring
```

Finally, I set this to be run on startup in the i3 config:
`xmodmap ~/.Xmodmap`

**My US keyboard is now 'ÆØÅ complete'**

![Letters and dancing: Æ-Ø-Å](/ae-oe-aa.png)

