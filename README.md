# **O2EM-Web**

This emulator is based on the O2EM and O2EM-NG emulators, which have been ported to a web version using emsdk.

## Requirements
- Have emsdk downloaded.
- Have SDL3 libraries in emsdk or on the OS.
- Have Cmake installed.

## How to build?
To compile and build the project, run the following command in your terminal (Windows):
```bash
mkdir build-wasm
cd build-wasm
cmake make .. ninja
ninja
```
- After you can get the wasm, js, html and data file.
