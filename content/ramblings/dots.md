---
title: my dotfiles
date: 2024-03-10
draft: false
tags: [meta, tech]
---

i spent an embarrassing amount of time moving pixels around so i wouldn't have to move my hands around. here's what stuck.

## speed, consistency, and stubbornness

terminal-first on macOS. themed in gruvbox because at some point you just pick a palette and stop thinking about it. **Gruvbox Dark** specifically, easier on the eyes for those late night coding sessions where you realize it's 4am and you were supposed to sleep three hours ago.

## kitty

switched to [kitty](https://sw.kovidgoyal.net/kitty/) from alacritty. it's written in python and uses OpenGL, which sounds like someone made a joke but actually works great. here's what i run with:

```kitty
font_family      MesloLGS Nerd Font Mono
font_size        18.0
cursor_shape     block
cursor_shape_unfocused hollow
hide_window_decorations yes
```

font size 18 because my eyes are bad and i refuse to get glasses. block cursor feels right, unfocused windows get the hollow one so you can tell where you are when you're bouncing between six tmux panes. hide_window_decorations keeps it clean.

i still keep my alacritty config around. rust-based, gpu-accelerated, genuinely fast. moved to kitty because cross-platform support and the config system doesn't make me want to throw my keeb out the window. old habits die hard.

## tmux

[tmux](https://github.com/tmux/tmux) is the reason i don't lose my mind. prefix remapped to ctrl+a because ctrl+b is a crime against your left hand. vim navigation because leaving home row is for chumps. windows renumber automatically so you don't get gaps and spend twenty minutes trying to remember why there's a hole between 2 and 4.

the plugin situation:

- [tpm](https://github.com/tmux-plugins/tpm) because managing plugins by hand is a special kind of pain
- [tmux-sensible](https://github.com/tmux-plugins/tmux-sensible) for defaults that don't require a phd
- [tmux-pomodoro-plus](https://github.com/olimorris/tmux-pomodoro-plus) for the timer in the status bar so i can pretend i have discipline
- [vim-tmux-navigator](https://github.com/christoomey/vim-tmux-navigator) for ctrl+hjkl pane switching. seamless.
- [tmux-resurrect](https://github.com/tmux-plugins/tmux-resurrect) and [tmux-continuum](https://github.com/tmux-plugins/tmux-continuum) because i crash my machine often enough that manual session recovery is not a viable lifestyle

## karabiner

on macOS, [karabiner elements](https://karabiner-elements.pqrs.org/) is the only way to make the keyboard feel like it belongs to you instead of apple.

### the hyper key

caps lock as hyper (shift+cmd+ctrl+option). this is the one modifier combo no app uses by default, so you get a whole new set of shortcuts without accidentally closing your browser or something stupid.

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

tap it once = escape. hold it = hyper. vim-friendly, which is the whole point.

### vim arrows and the launcher

hyper + h/j/k/l = arrow keys. keeps hands on home row, less strain, stays in flow state.

my favorite trick is hyper + o then another key for apps: d for discord, f for firefox, e for finder, m for music, a for arc, w for whatsapp. no mouse, no alfred, no spotlight. just type and it opens. karabiner's simultaneous key detection is clean enough that it feels like magic even though it's just a json file.

## fastfetch

[fastfetch](https://github.com/fastfetch-cli/fastfetch) because neofetch stopped getting updates and i'm too emotionally attached to the ritual of seeing a custom ascii penguin every time i open a terminal. ascii is stored separately so it's easy to swap out when i get bored.

## the gruvbox thing

tmux, kitty, alacritty, all gruvbox. warm, earthy, retro but readable. **Gruvbox Material Dark Medium** specifically. original gruvbox is a bit harsh, this one is softer. i've tried other themes. i always come back. there's probably a lesson there about attachment to familiar things but let's not get philosophical about a color scheme.

## compromises

this setup has sharp edges. no iterm2 because kitty does everything i need and i don't want to learn another app's quirks. no fuzzy finder in terminal because launcher mode covers it and adding more tools feels like clutter. very keyboard-heavy. if you like the mouse, this setup will feel hostile. it kind of is.

## closing

your dotfiles should feel like home. don't just clone someone else's repo and call it a day. steal what works, break what doesn't, make it yours. that's the whole point.

repo's linked if you want to steal anything. thanks for reading.
