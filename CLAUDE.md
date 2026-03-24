# SteelBook Designer Desktop App

## What This Is
Electron wrapper around the SteelBook Cover Designer web app, packaged as a portable Windows .exe.

- **Web app source:** https://github.com/Doolanjw/steelbook-designer
- **Live version:** https://doolanjw.github.io/steelbook-designer/
- **Author:** Jonathan Doolan

## Project Structure
- `main.js` — Electron main process (window creation, menu)
- `index.html` — The full web app (single self-contained HTML file, ~300KB)
- `package.json` — Electron + electron-builder config
- `dist/` — Build output (gitignored)

## Key Commands
- `npm run start` — Launch the app in dev mode
- `npm run build` — Build portable .exe → `dist/SteelBook-Designer-Portable.exe`
- `npm run build-installer` — Build NSIS installer .exe

## Build Notes
- **Windows symlink issue:** electron-builder's winCodeSign extraction fails without admin/developer mode due to macOS symlinks in the archive. Fix: pre-extract the cache at `%LOCALAPPDATA%\electron-builder\Cache\winCodeSign\winCodeSign-2.6.0` manually and ignore symlink errors.
- **No icon yet.** To add one: create a 256x256 .ico file as `icon.ico` and add `"icon": "icon.ico"` back to the `build.win` section of package.json.

## The Web App Features
- Upload/Edit panels for front, back, spine, interior covers
- AI Generate (DALL-E 3, Stability AI, Together AI/FLUX) and AI Remix
- Production assets: format logos, ratings, audio badges, UPC barcodes
- Spine Designer with custom text, colors, fonts, logos
- Project Manager: save/load .steelbook files
- Export: PNG (300 DPI), PDF with crop marks

## G2 SteelBook Dimensions
- Front/Back: 136mm × 171.4mm
- Spine: 8.7mm × 154.2mm
- Full wrap: 280.7mm × 171.4mm
- Bleed: 3mm
