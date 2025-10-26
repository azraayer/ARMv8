# ARMv8 Project

Brief: An ARMv8-A (A64) emulator and two‑pass assembler, a Raspberry Pi LED blink demo that runs on real Pi hardware, and an optional MNIST neural-net + graphics extension. Includes build scripts, tests, examples, and documentation.

## Features
- Emulator: fetch/dispatch loop, full machine state, handlers for data-processing, branches, loads/stores
- Assembler: two-pass tokenizer, symbol table, instruction encoders, binary output
- Raspberry Pi: A64 LED blink example (rpi/led_blink.s)
- Extension: MNIST NN + visualization (src/nn/, src/graphics/)

## Requirements
- Linux (development tested)
- gcc/clang, make, Python3 (for tools/scripts)
- Optional: Raspberry Pi running AArch64 for hardware demo

## Quick build
Build emulator:
  cd src/emulator && make

Build assembler:
  cd src/assembler && make

Build extensions (optional):
  cd src/nn && make
  cd src/graphics && make

## Assemble & run locally
1. Assemble an A64 source:
   cd src/assembler
   ./assembler ../../rpi/led_blink.s -o ../../rpi/led_blink.bin

2. Run in emulator:
   cd src/emulator
   ./emulator ../../rpi/led_blink.bin

Adjust paths/flags to match local binaries.

## Run on Raspberry Pi (hardware)
1. Use assembler to produce A64 binary (see above).
2. Copy binary to Pi (scp) and follow the hardware run steps in doc/Report.tex and README notes (GPIO setup and required privileges).

## Tests & examples
- Example assembly: rpi/led_blink.s
- Unit tests / small test programs located in respective src/* subdirs. Run `make test` where available.

## Project structure
- src/emulator/ — emulator sources & Makefile
- src/assembler/ — assembler sources & Makefile
- rpi/ — Raspberry Pi assembly examples
- src/nn/, src/graphics/ — extension code (MNIST + visualization)
- doc/ — report, design notes, and build/run instructions

