---
title: my dotfiles
date: 2024-03-10
draft: false
tags: [meta, tech]
---

been meaning to write this one for a while. every dev eventually builds their own environment, so here's mine.

## the big picture

speed, keyboard efficiency, visual consistency. terminal-first on macOS, themed in gruvbox because that's just what I do. **Gruvbox Dark Medium** specifically—easier on the eyes for those late night coding sessions.

## kitty (tty)

switched to [kitty](https://sw.kovidgoyal.net/kitty/) from alacritty. it's written in python and uses OpenGL, which sounds weird but works great. here's what I run with:

```kitty
font_family      MesloLGS Nerd Font Mono
font_size        18.0
cursor_shape     block
cursor_shape_unfocused hollow
hide_window_decorations yes
```

font size 18 because I like being able to read things. block cursor feels right, unfocused windows get the hollow one so you can tell where you are. hide_window_decorations keeps it clean.

## the alacritty backup

used alacritty before kitty. rust-based, gpu-accelerated, really fast. moved to kitty because I wanted better cross-platform support and the config system is nicer. still keep my alacritty config around, you know, just in case.

## tmux (tty multiplexer)

[tmux](https://github.com/tmux/tmux) is essential for managing sessions, windows, and panes. my setup:

- prefix remapped to ctrl+a (way better than ctrl+b)
- vim navigation because leaving home row is for chumps
- windows renumber automatically so you don't get gaps

### plugins

the good stuff:

| plugin                                                                  | purpose                  |
| ----------------------------------------------------------------------- | ------------------------ |
| [tpm](https://github.com/tmux-plugins/tpm)                              | plugin manager           |
| [tmux-sensible](https://github.com/tmux-plugins/tmux-sensible)          | defaults that don't suck |
| [tmux-pomodoro-plus](https://github.com/olimorris/tmux-pomodoro-plus)   | timer in status bar      |
| [vim-tmux-navigator](https://github.com/christoomey/vim-tmux-navigator) | ctrl+hjkl pane switching |
| [tmux-resurrect](https://github.com/tmux-plugins/tmux-resurrect)        | save sessions            |
| [tmux-continuum](https://github.com/tmux-plugins/tmux-continuum)        | auto-save every 15 min   |

the pomodoro plugin is useful—shows up right in the status bar so you can see where you are without breaking focus.

## karabiner elements (keybind remapping)

on macOS, [karabiner elements](https://karabiner-elements.pqrs.org/) is the way to go for key remapping.

### the hyper key

caps lock as hyper (shift+cmd+ctrl+option). this is the one modifier combo no app uses, so you get a whole new set of shortcuts without conflicts.

```json
{
  "description": "CAPS_LOCK to HYPER (SHIFT+COMMAND+OPTION+CONTROL) or ESCAPE (If Alone)",
  "manipulators": [
    {
      "from": { "key_code": "caps_lock" },
      "to": [
        { "key_code": "left_shift", "modifiers": ["left_command", "left_control", "left_option"] }
      ],
      "to_if_alone": [{ "key_code": "escape" }],
      "type": "basic"
    }
  ]
}
```

tap it once = escape. hold it = hyper. vim-friendly, which is the point.

### vim arrows

hyper + h/j/k/l = arrow keys. keeps hands on home row, less strain, stays in flow state.

### the "o" launcher

my favorite. hyper + o then another key launches apps:

- hyper + o + d = discord
- hyper + o + f = firefox
- hyper + o + e = finder
- hyper + o + m = music
- hyper + o + a = arc
- hyper + o + w = whatsapp

karabiner's simultaneous key detection is clean. no mouse, no alfred, just type.

## fastfetch (sys info)

[fastfetch](https://github.com/fastfetch-cli/fastfetch) as neofetch isnt maintained anymore. custom ascii art + organized modules. ascii is stored separately so it's easy to swap out.

## the theme: gruvbox

tmux, kitty, alacritty—all gruvbox. warm, earthy, retro but readable. **Gruvbox Material Dark Medium** specifically—original gruvbox is a bit harsh, this one is softer on the eyes.

## trade-offs

everyone's setup has compromises. here are mine:

1. no iterm2—kitty does everything I need
2. no fuzzy finder in terminal—launcher mode covers it
3. very keyboard-heavy—if you like the mouse, this won't work for you

## closing

your dotfiles should feel like home. don't just copy someone else—take what works, make it yours.

repo's linked if you want to poke around. happy hacking!
