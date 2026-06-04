# Building Heretic2R on macOS

This project has been ported to macOS using the same POSIX-compatible system layer as the Linux port.

## Prerequisites

- **Homebrew**
- **CMake**: `brew install cmake`
- **SDL3**: `brew install sdl3`

## Build

```sh
cmake -S . -B build-macos -DCMAKE_BUILD_TYPE=Release -DSDL3_ROOT=$(brew --prefix sdl3)
cmake --build build-macos -j8
```

Note: Replace `-j8` with the number of CPU cores on your machine.

## Output Layout

The build produces the following layout in the `build/` directory:

- `build/`
    - `Heretic2R` (Executable launcher)
    - `quake2.dylib` (Engine)
    - `H2Common.dylib` (Common utilities)
    - `ref_gl1.dylib` (OpenGL renderer)
    - `snd_sdl3.dylib` (SDL3 sound backend)
- `build/base/`
    - `gamex86.dylib` (Game logic)
    - `Player.dylib` (Player logic)
    - `Client Effects.dylib` (Client-side effects)

## Running

You will need the original Heretic II game data (v1.06). Copy the `base` folder into the `build` directory (preserving the structure so you have `build/base/*.pak` etc.).

On macOS, the user data (configs, saves) will be stored in `~/Library/Application Support/Heretic2R`.
