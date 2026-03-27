---
title: my text editor
date: 2023-12-13
draft: false
images: [borah-nvim.webp]
tags: [meta, tech]
---

![my lazyvim fork](assets/borah-nvim.webp)

They say once you go vim-motions you cannot go back. It all started with me getting into touch-typing and making decent progress and then installing the vim emulation plugin on vscode (as I didn't want my hands to move from the home row on my keebs), and soon after I tried to tough it out I diving straight into vimtutor and getting my motions right.

I started with vanilla neovim (with packer), then tried a few configs off github and youtube, then went full into building my own. Eventually landed on lazyvim as a base as it handles the boring stuff (plugin management, lazy-loading) so you can focus on the actual config. This is my fork.

[Here](https://github.com/abhinavborah/borah-nvim) is the github repo!

As a disclaimer, I update this whenever I remember to, so things might be broken (you've been warned).

## the fork and what's different

It started as a clean lazyvim install which is great and works out of the box, but you can't leave well enough alone, right?

I put gruvbox on anything I see, and the same has been used here for the colorscheme instead of the default theme. It just works for me you know-

Some funny ascii art in the startup screen via snacks.nvim. Makes opening it feel less sterile, which is nice.

UI stuff: I prefer neo-tree on the right (more room for code + doesn't get in the way while toggling), lualine themed to match, incline for floating file info, noice with lsp borders, nvim-notify. Played around with transparency too. Currently off, but the option's there.

## dev stuff

codeium instead of copilot. `<C-g>` accepts, `<C-]>`/`<C-[>` cycles, `<C-x>` clears. Toggle with telescope when you need focus.

VimTeX for LaTeX with skim as the pdf viewer.

C++ workflow: clangd and cmake-language-server for lsp, plus `<F10>` to compile and run with address sanitizers:

```lua
vim.keymap.set("n", "<F10>", function()
  vim.cmd("w")
  vim.cmd("!g++ -fsanitize=address -std=c++17 -Wall -Wextra -Wshadow -DONPC -O2 -o %< % && ./%< < input.txt")
end, { noremap = true, silent = true, desc = "C++ compile/run with sanitizer" })
```

Reads from `input.txt` for quick testing. Saved me a bunch of time. The same is used for grokking leetcode problems locally.

render-markdown.nvim for live preview. lazygit integration so I don't have to leave the terminal. vim-tmux-navigator for pane jumping between neovim and tmux. vim-visual-multi for multi-cursor editing. Spell check on for text files, off for JSON.

Oh, `<Tab>` mapped to `%` for jumping between brackets.

## plugin structure

Split into modular files under `lua/plugins/`: colorscheme, coding, lsp, tex, ui. Easier to find what you need than hunting through one giant config.

## what you need

- neovim (I mean no-brainer)
- fzf
- lazygit (nicer git integration)
- a C++ compiler (I'm using gcc via homebrew on macOS) if you want the compile/run feature

## closing thoughts

lazyvim's a solid starting point. I wouldn't recommend copying my config wholesale, but the part of the point is making it yours. But if you're looking for a reference, there you go.
