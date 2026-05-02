---
title: crayte - a 3d renderer in C
date: 2024-05-18
draft: false
images: [hello-there.jpg]
tags: [tech]
---

Crayte (pronounced "create") (see how funny I am) is a real-time 3D renderer written in C. It uses SDL2 for windowing and input handling, with no other dependencies.

![crayte-working-demo](assets/crayte-demo.gif)

## why i built it

i needed a mini-project for my computer graphics course. the kind of thing you start because the syllabus says you should, except i actually got into it. wrote every line myself. my own hands + keebs, no gpt shenanigans. funnily enough that's rare to come by now a days. agents weren't as powerful when i started, which in hindsight was a blessing because i had to figure out why my cube looked like a trapezoid the hard way.

right now it displays a 3D cube using parallel projection. it runs a basic game loop that handles input and renders frames to a color buffer. that's the core functionality. the future plan, once i am motivated enough, is to add .obj file loading so i can render more than just a sad rotating box.

## what i used

plain C (C99 standard). SDL2 for windowing and input. CMake (>= 3.10) with pkg-config to make building less painful. no external math libraries—just vector structs for 2D and 3D operations, handwritten, probably with bugs.

## how it went

started with basic setup commits: a Makefile, a game loop, vector struct definitions. from there things grew slowly. vector math functions (dot products, normalization, all the linear algebra i thought i understood but clearly didn't). parallel projection logic for rendering 3D geometry to 2D screen space. a color buffer system with garbage collection so i wouldn't leak memory everywhere. a debug grid because without it i couldn't tell if the renderer was broken or if my math was.

the build system evolved from a simple Makefile to CMake because i got tired of manually linking SDL2 differently on macOS and linux. now it builds cleanly across platforms, or at least it did the last time i checked.

the codebase has roughly 18ish commits from init to where it is now. working renderer, separate source files for display logic, builds with CMake. small, readable, not a production engine. just a learning project that happens to compile and run.

```bash
mkdir -p build && cd build
cmake ..
cmake --build . --config Release
./bin/crayte
```

on macOS with Homebrew, SDL2 installs via `brew install sdl2`. CMake's pkg-config integration finds it automatically.

## who is it for

i didn't have any "stakeholder" in mind while building it. started because it seemed fun. if you're curious about how 3D rendering works at a low level, how vectors get projected, how a color buffer functions, how a game loop drives a renderer—this is a small, readable codebase to dig through. it's not a production engine. it's not going to compete with unity. it's a thing i made because i wanted to see if i could.

---

_Built with C and SDL2 (and with patience and love)_
