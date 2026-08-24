# melt-binaries

`melt` (MLT Framework command-line renderer) extracted from the official [Shotcut](https://www.shotcut.org/download/) releases, per OS — so a microservice can fetch a working `melt` without depending on a Docker image that installs MLT/Shotcut system-wide.

## Layout

This branch (`main`) has all three OS's binaries together, for reference:

```
windows/
  binary/   # just melt.exe alone
  full/     # melt.exe + everything it needs to run standalone (Qt/MLT/FFmpeg shared libs, mlt-7 module data, etc.)
linux/
  binary/   # just the melt executable alone
  full/     # melt + everything it needs to run standalone
macos/
  binary/   # just the melt executable alone
  full/     # melt + everything it needs to run standalone
```

`binary/` alone is likely NOT enough to run `melt` outside its original install folder — it dynamically loads shared libraries and `mlt-7` module/profile data at runtime. `full/` is the safe bet; `binary/` is kept for reference/smaller footprint experiments.

## Per-OS branches

Each of `windows`, `linux`, `macos` branches contains ONLY that OS's `binary/` and `full/` folders at the repo root — meant for a shallow, single-branch clone from a Dockerfile or deploy script:

```bash
git clone --branch linux --single-branch --depth 1 https://github.com/joseluisbz/melt-binaries.git
```

## Source

Extracted from official Shotcut release packages (Windows installer, Linux `.txz`, macOS `.dmg`) — see each OS folder for the exact version extracted.
