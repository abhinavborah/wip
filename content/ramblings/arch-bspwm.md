---
title: my (legacy) arch btw rice
date: 2022-06-08
draft: false
images: [bspwm-rice.webp]
tags: [meta, tech]
---

![my bspwm rice](assets/bspwm-rice.webp)

I spent way too many hours tweaking every pixel when I first got bspwm running on arch. There's something addictive about building your own environment from scratch; every keybind, every behavior, it all reflects how you actually work. This is my BSPWM + Polybar setup, themed in gruvbox because I am boring like that.

As a disclaimer, I haven't updated my dots for a while, so I'm not sure how it looks on a newer system. You'll have to figure that out for yourself.

[Here](https://github.com/abhinavborah/bspwm-dotfiles) is the github repo for the same!

## bspwm

The `bspwmrc` file is where it all begins. I used Greek letters for workspaces (α through κ) because I wanted to seem cool and mysterious which in hindsight, is somewhat pretentious(?). 2px borders, 5px gaps, keeps things clean without feeling sparse. Focused windows get that gruvbox yellow border, which I find nice.

Autostart runs the essentials: sxhkd for hotkeys, picom for smooth transitions, dunst for notifications, feh to cycle through wallpapers, polybar at the top, and a small script that nags me when the battery drops.

## sxhkd

This is where bspwm shines. I mapped home row keys for navigation, vim-style because why reach for arrow keys when your hands are already on the home row? `super + h/j/k/l` moves focus around, add shift to swap windows. Super as the modifier keeps everything under your thumb (quite literally).

Volume keys work out of the box, 5% increments feel right (at least to me personally). Here's a nice trick: hold shift while adjusting brightness and it triggers redshift at 4500K. No more bleeding eyes at 2am.

App shortcuts: firefox, chrome, codium, virt-manager, blueman. dmenu gets the gruvbox treatment too as the yellow highlight matches the focused border.

## urxvt

urxvt because it just works. Background at 95% opacity so wallpaper shows through, but text stays readable. `Hack Nerd Font` handles everything well. I configured all four variants (regular, bold, italic, bold italic) so apps don't fall back to ugly defaults when they need italics.

## polybar

My workspaces on the left, window title (truncated so it doesn't hog space) next to it. Right side has filesystem, memory, cpu, volume, battery with charging animations, and time in 24-hour format. The gruvbox palette ties it all together (yet again).

## picom and dunst

picom handles shadows, fading, inactive opacity so unfocused windows step back. Nothing flashy, just enough to feel polished. VSync enabled, xrender backend for broad hardware support.

dunst sits in the top-right corner with the yellow frame. Normal ones timeout after 10 seconds, critical ones stick around until you deal with them. Blends in with the rest of the theme.

## things i still think about

An install script would be nice. network modules in polybar would be handy. theme switching for variety. The scripts directory I mention isn't in the repo. Wayland isn't happening since bspwm is X11 only, which is fine by me.

Took a while to get right, but the keyboard-driven workflow pays off. The consistent theming makes everything feel like one environment instead of a bunch of tools duct-taped together. If you want a reference bspwm setup with polybar and picom, this should give you a solid starting point.

You'll need Hack Nerd Font and the packages listed in the README of the project repo.

if you end up using any of this, let me know. or don't. either way, thanks for reading.
