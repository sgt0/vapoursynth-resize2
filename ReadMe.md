# resize2

`resize2` extends the standard zimg resizer with custom kernel support (user-defined kernels via a function),
a blur parameter to widen filter taps, and force-resize flags for overriding zimg's no-op checks.

## Installation

Pre-compiled wheels are available on PyPI for:

- **Windows**: x86_64
- **Linux**: x86_64 and aarch64
- **macOS**: arm64 (14.0+)

```bash
pip install vapoursynth-resize2
```

## Compilation

### Windows

Requirements:

- [MSYS2](https://www.msys2.org/)

1. Open **MSYS2 MINGW64** terminal.
2. Install dependencies:

   ```bash
   pacman -S mingw-w64-x86_64-{cmake,meson,ninja,pkgconf,gcc,vapoursynth,uv}
   ```

3. Build the wheel:

   ```bash
   uv build --wheel -Csetup-args="-Dlink-static=true"
   ```

### Linux & macOS 

Requirements:

- [Nix](https://nixos.org/)

```bash
nix develop -c uv build --wheel
```
