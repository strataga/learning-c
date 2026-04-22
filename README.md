# C Systems Programming: The Great Reset
> "A 28-year senior full stack web/mobile developers journey back to the metal primarily to learn game development."

This repository is a dedicated space for learning **C99** from scratch, moving away from high-level abstractions to master manual memory management, pointers, and systems-level architecture.

## 🎯 The Mission
The goal is to move from the "what" of web applications to the "how" of computer hardware, eventually building a grid-based pseudo-3D engine inspired by classics like *Dungeon Master* and *Wolfenstein 3D*.

## 🛠 Tech Stack & Environment
- **Standard:** C99 (`-std=c99`)
- **Compiler:** GCC (MinGW-w64 on Windows / WSL2)
- **Editor:** VS Code + Extensions (see below)
- **Build Tool:** Make (transitioning from manual CLI commands)
- **Debugger:** LLDB

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
gcc -o build/app src/main.c
./build/app
```

`-g:` - Adds debugging information so you can use tools like GDB to step through your code.

`-o` - What you want the program file to be named when it compiles.

>See the compile_flags.txt pro tip below.

I use visual studio code (vscode) because its lightweight and fast, so there is a .vscode directory with two files: launch.json and tasks.json. They hold the config on how you want to setup debugging. I prefer setting breakpoints and stepping through code inside vscode. To debug you would hit F5 (or fn+F5), or Cmd + Shift + B to select the task, or choose the debugging icon in the side menu (looks like a play button and a bug), and choose the appropriate task in the drop down menu - either a full program or just a file - and hitting the debug play button.

## References

The original K&R is for historical reference. The primary books are the other two.

- ["The C Programming Language - Second Edition (K&R)" by Brian W. Kernighan and Dennis M. Ritchie](https://github.com/auspbro/ebook-c/blob/master/The.C.Programming.Language.2Nd.Ed%20Prentice.Hall.Brian.W.Kernighan.and.Dennis.M.Ritchie..pdf)
- ["C Programming: A Modern Aproash" by K. N. King](https://github.com/Embed-Threads/Learn-C/blob/main/books/c-programming-a-modern-approach-2nbsped-0393979504-9780393979503_compress.pdf)
- ["21st Century C" by Ben Klemens](https://karadev.net/uroci/filespdf/files/21st-century-c-o-reilly-ben-klemens.pdf)

> copies of the pdfs are in the reference folder

## Linting and Formatting

Linting in C helps catch bugs. For a modern vscode setup, the recommended way to handle linting and static analysis is through **clang-tidy** and **clang-format**. 

You have two main paths depending on how "deep" you want to go into the C ecosystem:

1. The Integrated Path (Microsoft C/C++ Extension) 
Since you already have the official C/C++ extension installed, you can enable its built-in clang-tidy support. 

    How to enable: Open your settings (Cmd + ,), search for C_Cpp: Code Analysis: Clang Tidy: Enabled, and set it to true.

    Automatic checks: Set Clang Tidy: Run On Save to true. Now, whenever you save your file, VS Code will run background checks for memory leaks, uninitialized variables, and style violations. 

2. The "Pro" Systems Path (clangd Extension)
Many veteran C developers prefer the clangd extension over Microsoft's default IntelliSense because it is faster and uses the same "engine" that powers the compiler. 

    Best feature: It provides real-time "Fix-its"—it doesn't just show an error; it often provides a lightbulb icon you can click to automatically fix the code.

    Setup: Install the clangd extension. It will ask to disable the default Microsoft IntelliSense; say Yes. 

3. Formatting (Style Linting)
To ensure your code looks clean (consistent indentation, bracket placement), use clang-format. 

    Setup: Create a .clang-format file in your project root. You can generate a default one with the command line: clang-format -style=llvm -dump-config > .clang-format.

    Format on Save: In VS Code settings, enable Editor: Format On Save.

## VSCode Extensions

1. Code Intelligence & Navigation
- clangd: Provides the best "Go to Definition," "Find References," and real-time error checking for C.
- Include AutoComplete: Helps you quickly find headers like <stdio.h> or <stdlib.h> as you type.

2. The "Handmade" Game Dev Essentials
- MemoryView: This is critical for your "reset." It lets you see a "Hex Dump" of your computer's RAM while debugging. If you want to see exactly how your Monster struct is stored in bytes, this is the tool.
- Hex Editor: Essential for a game developer. Use this to open and inspect binary game assets (like those WAD files or pixel art textures) directly in VS Code.

3. Build & Task Management
- Error Lens: Instead of just a red squiggle, this puts the compiler error message right on the line where it's happening. It’s the best way to catch missing semicolons instantly.
- Makefile Tools: As you move past single files and start building your dungeon crawler engine, you'll likely use a Makefile. This extension gives you a "Build" button in the sidebar.

4. Visuals & Readability
- Doxygen Documentation Generator: Type /** above a function and it generates a documentation block. Great for keeping track of your engine's logic as it grows.
- Better C++ Syntax: Don't let the name fool you; it provides superior color highlighting for C as well, making pointers and structs much easier to distinguish.

5. Extra
Todo Tree: Perfect for marking // TODO: Implement collision detection and finding it later in a sidebar.

## Pro Tips:
1. Master "MemoryView" (The Career Changer)
This is the single most important tool for a C developer.
- How to use it: Start your debugger (F5) and pause on a line where you have a variable or struct.
- The Power Move: Open the Memory View tab, and in the address bar, type the name of your variable (e.g., &myParty).
 - The Benefit: You will see the literal Hexadecimal bytes in RAM. You'll see exactly how an int takes up 4 bytes and how they are laid out in "Little Endian" order. This is how you learn why "Pointers" are just memory addresses.
2. Live Troubleshooting with "Error Lens"
You no longer need to check the "Problems" tab or wait for a compile to fail.
- How to use it: As you type, the error message will appear at the end of the line in a faint red or orange color.
- The Benefit: It trains your brain to catch the "C Tax" (missing semicolons, type mismatches) instantly. If you try to pass an int into a function expecting a pointer, Error Lens will shout at you before you even hit save.
3. Binary Auditing with "Hex Editor"
This is your "Dungeon Master" asset inspector.
- How to use it: Right-click any non-text file (like an image or a binary data file) and select "Open With... Hex Editor."
- The Benefit: You can see how data is structured on disk. Later, when you create a .dat file to store your dungeon maps, you’ll use this to verify your code is writing the bytes in the correct order.
4. Semantic Highlighting with "Better C++ Syntax"
- How to use it: Ensure your "Color Theme" supports semantic highlighting (most modern ones do).
 - The Benefit: It will color-code Members (like myParty.health) differently than Local Variables. In a 500-line game engine file, this visual "scaffolding" helps you navigate complex structs much faster than plain text.
5. Documentation via "Doxygen"
- How to use it: Position your cursor above a function and type /** then hit Enter.
- The Benefit: It forces you to document the Inputs and Outputs of your functions. In web dev, we often rely on descriptive variable names; in C, where you are passing pointers and memory buffers, documenting who owns the memory you just passed is vital.
6. The "compile_flags.txt" trick for Clangd
Clangd needs to know your "Standard" to give you the right hints.
Create a file named compile_flags.txt in your project root.
    ```
    -xc
    -std=c99
    -Wall
    -Wextra
    -Wpedantic
    -Wshadow
    -Wconversion
    -Werror
    -I/usr/local/include
    -I/Library/Developer/CommandLineTools/usr/include
    ```

    Why these specific flags?
    - `-xc`: Language: C - Explicitly tells clangd "this is C code" (sometimes it can get confused with C++).
    - `-std=c99`: C99 Standard - Ensures the linter matches your project's version of C.
    - `-Wall` : Warnings: All - Enables the "standard" set of warnings (e.g., unused variables).
    - `-Wextra`: Warnings: Extra - Catches subtle logic issues that -Wall misses.
    - `-Wpedantic`:  Pedantic - Rejects non-standard "shortcuts" and enforces strict C rules.
    - `-Wshadow`: Shadowing - Warns if you name a variable the same as one in an outer scope.
    - `-Wconversion`: Type Conversion - Warns if you might lose data (e.g., shoving a big int into a small char).
    - `-Werror`: Warnings as Errors - (Optional) Forces you to fix every warning before it allows a build.
    - `-I...`: Include Path - 	Tells the compiler where to look for system headers (like stdio.h).

    > make sure to press `CMD + Shift + P`, type `clangd: Restart language server` and select it (or hit enter)