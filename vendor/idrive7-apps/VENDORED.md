# idrive7-apps (vendored)

The runtime, GPU renderer, emulator and installer of
[idrive7-apps](https://github.com/cauliflowermossgrape/idrive7-apps) by cauliflowermossgrape (MIT, see LICENSE),
at commit `5555ef3bd2195aae15a8cec6803beeb40ca16456` (2026-11-18), shared by the three apps of this repository.
This version of the kit builds the iDrive 8 screen description (`uiDescriptions/ID8`) and places the drawing on
iDrive 8's 2880 x 960 screen (`kit/runtime/display.js`, `HMI8`).

Left out to keep the repository small: the kit's own apps (`apps/`, where each app's `tools/setup.js` links its
`app/` on a PC and the build copies it), its documentation (`docs/`), Doom's sources (`third_party/`), the
translated READMEs and the translated diagnostic texts (`kit/localization/diagnostic-full.*.json`), none of which
these apps use.

The patches in `../../patches/idrive7-apps/` are applied:
- `emulator-windows-and-diagnostics.patch`: the emulator on Windows and its diagnostics hook (as in mgu-apps);
- `id8-wide-page-emulator-manifest.patch` (this repository's): on iDrive 8 a screen with `"wide": true` gets a page as
  wide as the area allows (about 2200 x 520 logical px instead of 1600 x 520, read with `ctx.pageWidth()`; the
  settings sheet follows it); `build.py` writes app.json's `mguHmi`, `needs` and `requires` into the package's
  `package.json` (`mguHmi`, `mguNeeds`, `mguRequires`); the emulator takes `--id8` (a 2880 x 960 screen with iDrive
  8's status and climate bars, the app area 0,76 2880x764, no controller gate).
