# melt-binaries — full

Complete decompressed Shotcut v26.8.1 package per OS — includes the full GUI app, preview/playback (SDL2), capture card (Decklink), OpenCV, Whisper transcription, and every MLT module, most of it unused by a headless `melt` render.

For a microservice/Docker use case, use the `minimo` branch instead — same `melt`, ~3-4x smaller, traced against real usage (see `main` branch README).

```
windows/   full extracted shotcut-win64-26.8.1.zip
linux/     full extracted shotcut-linux-x86_64-26.8.1.txz (symlinks dereferenced to real files — Windows/git can't store them, so this is ~1.7x the original's on-disk size)
macos/     full extracted shotcut-macos-26.8.1.dmg
```
