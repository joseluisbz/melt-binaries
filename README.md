# melt-binaries — win-min

Minimal working set of `melt.exe` for Windows — just enough to render an `.mlt` project to `.mp4` headlessly. See `main` branch for how this was determined. Verified working (real render) 2026-08-25.

```bash
git clone --branch win-min --single-branch --depth 1 https://github.com/joseluisbz/melt-binaries.git
```

## Requisitos de runtime

Solo una variable de entorno hace falta (Qt necesita un modo sin ventana para correr headless; `qt.conf`, ya incluido junto a `melt.exe`, resuelve solo las demás rutas):
```powershell
$env:QT_QPA_PLATFORM = "offscreen"
```

## ffmpeg.exe / ffprobe.exe

Incluidos en la raíz (mismo nivel que `melt.exe`), copiados directamente de `win-full` (idéntico binario). No son necesarios para renderizar — `melt` no los invoca — pero sí para validar el `.mp4` resultante (duración/resolución reales vía `ffprobe`) antes de darlo por bueno.
