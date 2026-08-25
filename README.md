# melt-binaries — lnx-min

Minimal working set of `melt`/`melt-7` for Linux — just enough to render an `.mlt` project to `.mp4` headlessly. See `main` branch for how this was determined. Verified working on AlmaLinux 10 (glibc 2.39) 2026-08-25.

Requires glibc >= 2.35 (Ubuntu 22.04+, Debian 12+, Oracle/RHEL/Rocky/Alma 10+ — NOT 9.x).

```bash
git clone --branch lnx-min --single-branch --depth 1 https://github.com/joseluisbz/melt-binaries.git
```

## Requisitos de runtime

Variables de entorno (`melt` en Linux tiene grabada una ruta absoluta del servidor donde se compiló Shotcut — sin esto, termina en exit 0 sin generar nada, sin error claro):
```bash
export LD_LIBRARY_PATH="$(pwd)/lib"
export QT_QPA_PLATFORM=offscreen
export QT_PLUGIN_PATH="$(pwd)/lib/qt6"
export MLT_REPOSITORY="$(pwd)/lib/mlt-7"
export MLT_DATA="$(pwd)/share/mlt-7"
```

Paquetes de sistema pequeños (NO son mlt/ffmpeg/shotcut, son librerías genéricas del SO — instalar en el Dockerfile del microservicio, no aquí):

**RHEL/AlmaLinux/Rocky/Oracle 10+ (`dnf`):**
```
alsa-lib libX11 libdrm mesa-libgbm libwayland-egl libwayland-client
libwayland-cursor libX11-xcb libxcb libgpg-error libglvnd-glx
libglvnd-opengl libglvnd-egl fontconfig freetype libva cairo
```

**Debian/Ubuntu (`apt`) — equivalentes, sin verificar en un Ubuntu real todavía:**
```
libasound2t64 libx11-6 libdrm2 libgbm1 libwayland-egl1 libwayland-client0
libwayland-cursor0 libx11-xcb1 libxcb1 libgpg-error0 libglx-mesa0 libegl1
libgl1 libfontconfig1 libfreetype6 libva2 libcairo2
```
