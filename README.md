# OneSauceThemes — XMB Blue

An XMB-inspired One saUCE / RetroFE theme for Christine's AtGames Legends Ultimate, designed on a 1920 × 1080, 16:9 canvas.

The first pass takes its direction from the PSP and PS3: a quiet blue wave, white category icons, generous space, and a vertical list under the selected category. It reuses the supplied Renee pack's font, sounds, system logos, and device artwork.

![XMB Blue preview](docs/preview.png)

## Use

- Install the `layouts/XMB Blue` folder following [INSTALL.md](INSTALL.md).
- Open `preview/index.html` in a desktop browser for an interactive sample library. Arrow keys, Enter, and Escape work; the preview does not launch games.
- Ready-to-copy ZIPs are produced locally in `dist/` by the packaging command below.

## Navigation

At the root, Left/Right selects a category. A / Start enters it. Up/Down then selects systems or games; A / Start enters or launches, and Rewind returns. Deeper lists reuse the same vertical layout. Existing collection order, game lists, media, and control mappings come from the installed One saUCE setup.

This first version follows RetroFE's Select/Back hierarchy. Returning to the category row requires Back; it does not implement the original Sony XMB's simultaneous two-axis navigation.

## Edit and rebuild

The ready-to-use theme files are committed. No build tools are needed on the cabinet.

```bash
python3 tools/build.py
npm install --no-save sharp
python3 -m pip install Pillow
node tools/render-art.cjs
python3 tools/validate.py
python3 tools/build.py --package
```

- `tools/build.py`: layout geometry, menu transitions, category definitions, SVG generation.
- `src/art/`: editable vector source for the blue background, wave, focus glow, and original icons.
- `layouts/XMB Blue/`: generated XML/PNG assets and imported Renee assets.
- `preview/`: browser preview of the same artwork and geometry, with a small illustrative library.
- `src/base-import.json`: provenance and hashes of the reused assets.

To reimport the supplied original assets, extract `Base.zip` and run `python3 tools/build.py --base /path/to/Renee`. The importer includes only the font, two sounds, logos, and device art referenced by this design. It does not import Renee's old collection-specific layouts or the duplicate nested archive.

## Verification

XML, static asset references, PNG decoding, source-asset hashes, menu structure, and the installation ZIP are checked by `tools/validate.py`. The browser preview is exercised with keyboard navigation and missing-media checks. Validation of the actual cabinet rendering and input behavior is still pending; the browser preview is a design simulation, not a RetroFE emulator.

No ROMs, game screenshots, or game videos are included. The theme reads those from the user's existing collections.

See [CREDITS.md](CREDITS.md) for asset provenance and implementation references.
