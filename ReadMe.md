# resize2

`resize2` extends the standard zimg resizer with custom kernel support (user-defined kernels via a function)
a blur parameter to widen filter taps, and force-resize flags for overriding zimg's no-op checks.

# Compilation
```bash
meson setup build
meson compile -C build
```

Static build:

```bash
meson setup -Dlink-static=true build
meson compile -C build
```
