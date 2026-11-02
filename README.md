# FLOPPA CAPS — Flydigi Vader 4 Pro controller overlay

First functional **prototype**, derived from the workflow of [Stract Controller Overlay](https://github.com/gfgggggggghhjred/Stract-controller-overlay). Original repository was not modified or copied. This version is newly implemented, using the approved mockup image as artwork.

## Included
- `index.html` — self-contained transparent Canvas overlay and standard Gamepad API handling; no install or build process.
- `assets/vader4_skin.png` — cutout of the approved purple/white FLOPPA CAPS Vader 4 Pro **mockup**.
- `preview.jpg` — non-transparent design preview.

## GitHub Pages deployment (no Python required)

1. On GitHub, create a **public** repository, for example `Floppa-Vader4-Overlay`.
2. Upload **the contents** of this folder (not the ZIP as a single file) to the repository root. The repository should have `index.html` at the top level, plus `assets/vader4_skin.png`.
3. In your repository, open **Settings → Pages**. Select **Deploy from a branch**, then branch **main**, folder **/(root)**, and save.
4. After publishing, the overlay URL will look like `https://YOUR-USERNAME.github.io/Floppa-Vader4-Overlay/` (repository capitalization and URL paths must match).
5. In OBS, add a **Browser Source** using that **Pages URL** (not the GitHub repository URL). Set width **1672**, height **941** and FPS **60**.
6. To test animated visual alignment without controller input, open `https://YOUR-USERNAME.github.io/Floppa-Vader4-Overlay/?test=1`. To inspect detected controller data, use `?debug=1`.

**Important Gamepad API limitation:** GitHub Pages will host the transparent overlay and its animation code, but it does **not** forward controller events from your gaming PC to OBS. OBS's embedded Chromium may not expose gamepads in a Browser Source. Verify actual input with `?debug=1` in OBS. A supported browser may detect the controller, but browser-window capture or a separate local gamepad-to-web input bridge may be needed for reliable OBS input. Simply hosting it on Pages does not guarantee working controller inputs.

`?pad=0` chooses the first gamepad (zero-based index) when several are connected.

## Updating the design

Push changes to `index.html` or `assets/vader4_skin.png` and GitHub Pages redeploys automatically. You can retain the **same** OBS URL. If OBS shows old graphics, refresh the Browser Source cache.

## Mapping
Standard XInput-like Gamepad API: A=0, B=1, X=2, Y=3; LB/RB=4/5; LT/RT=6/7 (analog value); View/Menu=8/9; L3/R3=10/11; D-pad up/down/left/right=12/13/14/15; Home=16 if available. Left stick axes 0/1; right stick 2/3. C/Z and rear buttons **are not guaranteed to be exposed separately** by standard Gamepad API. They currently glow only in animation test mode, pending a controller-specific bridge/mapping.

## Design limitations / next refinement
- Cutout is based on a generated **concept**, not a pixel-perfect photograph or vector template of the real Flydigi Vader 4 Pro. Button and silhouette geometry need calibration against a real controller image.
- The printed meme art and text are baked into the concept preview; for 1:1 fidelity, supply a flat controller template / source layered artwork.
- Stick travel is an approximate 19-pixel motion simulation and should be calibrated during testing.
- Input behavior has been implemented but not hardware-tested. No guarantee of OBS browser engine Gamepad API support.
- No original source code from Stract was reused because a complete local checkout could not be downloaded in this environment.
