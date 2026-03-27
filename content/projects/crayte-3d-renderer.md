---
title: crayte - a 3d renderer in C
date: 2024-05-18
draft: false
images: [hello-there.jpg]
tags: [tech]
---

Crayte (pronounced "create") (see how funny I am) is a real-time 3D renderer written in C. It uses SDL2 for windowing and input handling, with no other dependencies.

![crayte-working-demo](assets/crayte-demo.gif)

## What it does

The renderer displays a 3D cube (at least for the time being) using parallel projection. It runs a basic game loop that handles input and renders frames to a color buffer. That's the core functionality.

The future plan (once I am motivated enough) is to add an important functionality for the .obj files, which will then be rendered on the screen.

The project was supposed to be a proof-of-concept/mini-project for my computer graphics course. I had fun coding it (my own hands + keebs, no gpt shenanigans), funnily enough which is rare to come by now a days (not to mention the fact that agents weren't that powerful when I had started working on it).

## Tech stack

- **Language:** C (C99 standard)
- **Windowing/Input:** SDL2
- **Build System:** CMake (>= 3.10) with pkg-config for dependency resolution
- **Math:** vector structs for 2D and 3D operations, oh and no external math libraries

## How it started

The project began with basic setup commits: a Makefile, a game loop, vector struct definitions. From there, things were eventually added:

- vector math functions (dot products, normalization, etc.)
- parallel projection logic for rendering 3D geometry to 2D screen space
- a color buffer system with garbage collection for memory management
- a debug grid for testing

The build system evolved from a simple Makefile to CMake, making it easier to build across macOS, Linux, and other platforms.

## Current state

The codebase has a working renderer that can display a 3D cube. It's a small project with roughly 18ish commits from init to where it is now. The code is organized into separate source files (display logic split from main), and builds cleanly with CMake.

## Building it

```bash
mkdir -p build && cd build
cmake ..
cmake --build . --config Release
./bin/crayte
```

On macOS with Homebrew, SDL2 installs via `brew install sdl2`. CMake's pkg-config integration finds it automatically.

## Who is it for

While building it I didn't have any "stakeholder" in mind. Started building it because it seemed fun.

If you're curious about how 3D rendering works at a low level, how vectors get projected, how a color buffer functions, how a game loop drives a renderer then this is a small, readable codebase to dig through.

It's not a production engine (yet). It's a small learning project that happens to compile and run.

---

_Built with C and SDL2 (and with patience and love)_
