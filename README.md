# melt-binaries — lnx-full

Complete decompressed `shotcut-linux-x86_64-26.8.1.txz` — melt is at `bin/melt` (`bin/melt-7` is the real target, was a symlink in the original, dereferenced here so it survives Windows/git). Symlinks were dereferenced throughout, so this is larger on disk than the original tarball. See `lnx-min` for the trimmed set (recommended for deployment).

Requires glibc >= 2.35 (Ubuntu 22.04+, Debian 12+, Oracle/RHEL/Rocky/Alma 10+ — NOT 9.x).

```bash
git clone --branch lnx-full --single-branch --depth 1 https://github.com/joseluisbz/melt-binaries.git
```
