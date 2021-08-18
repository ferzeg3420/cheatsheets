---
title: C++ compiler
---

# The c++ compiler (on Unix at least). 

I hear there's another one called llvm or something

## Optimization modes and getting the assembly code

- g++ -S produces assembly code given cpp source code.
- g++ -S -O0
- g++ -S -O1
- g++ -S -O2
- g++ -S -O3  These produce different levels of optimized assembly code.

## A good way to use the compiler

g++ -Wall -Wextra -Wpedantic -Wshadow -Wold-style-cast # are good warnings.
g++ Werror // tells you if you're dereferencing nullptrs? I don't even know.

## Other flags

- g++ -c # produces object files for later linking (important in big projects).

- g++ -g # Lets you use gdb for debugging with the file being compiled.

- g++ -MM # gives you the formula necessary to compile something into an
object file.

- g++ -o # Links .o (object files) to make an executable from them.
