```bash
meson setup build
meson compile -C build
```

Static build:

```bash
meson setup -Dlink-static=true build
meson compile -C build
```
