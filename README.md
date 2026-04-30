# MyMisu OS - Browser Demo

Boot a real bare-metal x86 operating system in your browser. No download, no install.

**[Launch the demo](https://brago475.github.io/MyMisu_Demo/)**

---

## What is this?

MyMisu OS is a hobby operating system written from scratch in C and x86 assembly. This page hosts the OS running inside [v86](https://github.com/copy/v86), a JavaScript x86 emulator. When you click Start, your browser boots the actual ISO that boots on real hardware.

## How to use

1. Open [brago475.github.io/MyMisu_Demo](https://brago475.github.io/MyMisu_Demo/)
2. Click **Start MyMisu OS** and wait ~10 seconds for boot
3. Click inside the black screen to capture your keyboard
4. Login with **misu** / **misu**
5. Type `help` to see all 35+ commands

To release the keyboard, press `ESC` outside the screen area.

## Things to try

| Command | What it does |
| --- | --- |
| `help` | List every command grouped by category |
| `syscall` | Run all 19 system calls and show PASS/FAIL |
| `spawn all` | Spawn three concurrent kernel tasks |
| `top` | Live process viewer with CPU% (refreshes every 500ms) |
| `dmesg` | Show kernel log buffer with timestamped events |
| `tree` | Visualize the filesystem as a tree |
| `colors` | Print the VGA color palette |
| `snake` | Play snake (arrow keys, Q to quit) |
| `ttt` | Tic-tac-toe vs an unbeatable CPU |
| `widgets` | Desktop widgets dashboard |

## Demo flow (60 seconds)

1. `help` - shows the OS knows what it can do
2. `syscall` - 19 syscalls all PASS in green
3. `spawn all` - kicks off three kernel tasks
4. `top` - watch CPU% and states change in real time (this is preemptive multitasking)
5. `ESC` to exit top, `dmesg` to see what just happened
6. `tree` to see the filesystem

## Browser support

Works in any modern browser. Tested on Chrome, Firefox, Edge, and Safari. Mobile browsers also work but the on-screen keyboard makes input awkward.

Loading the OS uses ~6 MB of bandwidth on first load (then cached).

## Source code

This repo is just the demo page wrapper. The actual OS source lives at:

**[github.com/Brago475/myMisu_OS](https://github.com/Brago475/myMisu_OS)**

To run the OS yourself outside a browser:
qemu-system-i386 -cdrom mymisu.iso -m 128M
Or flash the ISO to a USB and boot real hardware.

## Files in this repo

- `index.html` - the demo page
- `mymisu.iso` - the OS image (built from the main repo)
- `libv86.js`, `v86.wasm` - the x86 emulator
- `seabios.bin`, `vgabios.bin` - BIOS firmware

## About MyMisu OS

A learning project. Bare-metal x86, monolithic kernel, real preemptive scheduler with x86 assembly context switching, 19 system calls via `int 0x80`, ramdisk filesystem with file descriptors, ~10K lines of C and assembly.

Built for CPS 5520 - Computer Systems and Concepts at Kean University, Spring 2026.

**Team:** James Mardi, Danny Munoz, Kyle Humlen
**Instructor:** Juan Li
