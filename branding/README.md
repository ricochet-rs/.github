# Branding

These files are the source for the ricochet logo across the website, the docs, the app, and the GitHub organization.
Copy a file from here into a project rather than redrawing or recolouring it.

| File             | Use it for                                                                 |
| ---------------- | -------------------------------------------------------------------------- |
| `logo.svg`       | Web pages and SVG favicons. The browser switches it to white in dark mode. |
| `logo-black.svg` | Light backgrounds where the viewer's colour scheme does not apply.         |
| `logo-white.svg` | Dark backgrounds where the viewer's colour scheme does not apply.          |
| `avatar.svg`     | The source of every square icon. Export raster sizes from this file.       |
| `avatar.png`     | The GitHub organization avatar and other profile pictures, at 1024 × 1024. |

## Square icons

Raster icons cannot follow the viewer's colour scheme, so every PNG and ICO icon uses the avatar tile: a black rabbit on an opaque white square.
A transparent icon disappears on dark browser tabs, and iOS fills transparency with black, which hides a black rabbit on the home screen.

Export the standard set from `avatar.svg` with Inkscape and ImageMagick:

```sh
# render each size from the tile
for s in 16 32 48 180 192 512; do inkscape avatar.svg -o $s.png -w $s -h $s; done
# drop the alpha channel so no platform fills it with its own colour
for s in 16 32 48 180 192 512; do magick $s.png -background white -alpha remove -alpha off -strip PNG24:$s.png; done
# bundle the small sizes into the ICO fallback
magick 16.png 32.png 48.png favicon.ico
```

Ship them as `favicon-16x16.png`, `favicon-32x32.png`, `favicon.ico`, `apple-touch-icon.png` (180), and `android-chrome-192x192.png` and `android-chrome-512x512.png`.
Keep `logo.svg` as `favicon.svg`, because browsers that support SVG favicons prefer it and it adapts to dark mode.
