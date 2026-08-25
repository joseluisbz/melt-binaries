# melt-binaries — mac-min

Minimal working set of `melt` for macOS — just enough to render an `.mlt` project to `.mp4` headlessly. See `main` branch for how this was determined. Verified working on a real Apple Silicon Mac (Rosetta 2, x86_64 build) 2026-08-25.

```bash
git clone --branch mac-min --single-branch --depth 1 https://github.com/joseluisbz/melt-binaries.git
```

## Requisitos de runtime

```bash
xattr -cr .          # quita la cuarentena de Gatekeeper (viene de GitHub)
chmod +x MacOS/melt
export QT_QPA_PLATFORM=offscreen
export QT_PLUGIN_PATH="$(pwd)/PlugIns/qt"
```

Si se queja de "no plugins found" o de perfiles faltantes:
```bash
export MLT_REPOSITORY="$(pwd)/PlugIns/mlt"
export MLT_DATA="$(pwd)/Resources/mlt"
```

**No re-firmar el binario** (`codesign --sign -`) — reemplaza la firma original de Apple/Meltytech por una ad-hoc, lo que rompe la confianza que Rosetta 2 necesita para traducir binarios Intel descargados de internet (produce "melt is damaged and can't be opened"). `qt.conf` ya está colocado junto a `melt` en `MacOS/`, que es donde Qt lo busca primero — evita que necesite consultar la estructura de bundle de macOS para nada.
