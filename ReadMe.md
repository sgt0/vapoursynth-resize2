# resize2

`resize2` extends the standard zimg resizer with custom kernel support (user-defined kernels via a function),
a blur parameter to widen filter taps, and force-resize flags for overriding zimg's no-op checks.

## Differences from Core Resize

### New Method

- **`Custom`**: Allows using a user-defined function as the scaling kernel.
  - `custom_kernel`: A callback function that takes an input position and returns an evaluated kernel value.
  - `taps`: The number of filter taps for the custom kernel.

### New Parameters

Added to all resizing methods:

- **`blur`** / **`blur_uv`**: Multiplier for the filter frequency. Values > 1.0 blur the image, while values < 1.0 sharpen it.
  `blur_uv` specifically affects chroma planes.

  Equivalent to `fh` and `fv` parameters of `fmtc`: `blur=1.5` == `fh=1 / 1.5, fv=1 / 1.5`

- **`force`** / **`force_uv`**: Boolean flag to force processing even when zimg would typically skip it. `force_uv` affects chroma.
- **`force_h`** / **`force_h_uv`**: Force horizontal processing specifically for luma or chroma.
- **`force_v`** / **`force_v_uv`**: Force vertical processing specifically for luma or chroma.

## Installation

Pre-compiled wheels are available on PyPI for:

- **Windows**: x86_64
- **Linux**: x86_64 and aarch64
- **macOS**: x86_64 and arm64 (13.0+)

```bash
pip install vapoursynth-resize2
```

## Compilation

```bash
uv build --wheel
```

On Windows you may want to add `-Csetup-args="--vsenv"` to the command.
