# C Systems Programming: The Great Reset
> "A 28-year senior full stack web/mobile developers journey back to the metal primarily to learn game development."

This repository is a dedicated space for learning **C99** from scratch, moving away from high-level abstractions to master manual memory management, pointers, and systems-level architecture.

## 🎯 The Mission
The goal is to move from the "what" of web applications to the "how" of computer hardware, eventually building a grid-based pseudo-3D engine inspired by classics like *Dungeon Master* and *Wolfenstein 3D*.

## 🛠 Tech Stack & Environment
- **Standard:** C99 (`-std=c99`)
- **Compiler:** GCC (MinGW-w64 on Windows / WSL2)
- **Editor:** VS Code + C/C++ Extension Pack
- **Build Tool:** Make (transitioning from manual CLI commands)
- **Debugger:** GDB

## 🏗 Project Roadmap
- [ ] **Phase 1: The Basics** (Hello World, Variables, Control Flow)
- [ ] **Phase 2: Memory & Pointers** (The "Paradigm Shock" phase)
- [ ] **Phase 3: Data Structures** (Structs, Enums, Typedefs)
- [ ] **Phase 4: File I/O & Assets** (Loading data without libraries)
- [ ] **Phase 5: The Raycaster** (Grid-based movement & rendering logic)

## ⌨️ Common Commands
> I'm learning on my Macbook so your commands may vary.

```bash
brew install gcc
```

To compile and run a single-file program:
```bash
gcc -std=c99 -Wall -g src/main.c -o build/app
./build/app
```

`-std` - Sets the C standard version. c99 is the defacto standard.

`-Wall` - Enabled most common warning messages - highly recommended to catch logical errors early.

`-g:` - Adds debugging information so you can use tools like GDB to step through your code.

`-o` - What you want the program file to be named when it compiles.

I use visual studio code (vscode) because its lightweight and fast, so there is a .vscode directory with two files: launch.json and tasks.json. They hold the config on how you want to setup debugging. I prefer setting breakpoints and stepping through code inside vscode. To debug you would hit F5 (or fn+F5), or choose the debugging icon in the side menu (looks like a play button and a bug), and choose the appropriate task in the drop down menu - either a full program or just a file - and hitting the debug play button.

