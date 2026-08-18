# Zen Photon Garden: demo build

A prebuilt, self-contained copy of Zen Photon Garden, cleaned up for a client demo. Nothing loads from a CDN and no analytics tracker is included.

## Run it

Any static file server works. From this folder:

```
python3 -m http.server 8000
```

Then open `http://localhost:8000`. Web Workers will not run from a `file://` URL, so you do need a server.

Basic interaction: drag on the canvas to draw a wall, and light accumulates against it. The light source is placed with the crosshair tool. Everything is in the toolbar along the bottom.

## Embedding in an existing site

Drop the whole folder in as a subdirectory (for example `/calm/`) and iframe it, or lift `index.html` into your own template. The runtime files you need are:

- `zenphoton.js` (main bundle)
- `rayworker.js` and `rayworker-asm.js` (render workers, loaded by path at runtime, so keep them as siblings)
- `roboto.ttf`
- the favicon and logo PNGs, if you want them

## Rebuilding after edits

Source lives in `src/`, written in CoffeeScript 1.x. To rebuild:

```
npm install coffeescript@1.12.7 jsmin
PATH=$PWD/node_modules/.bin:$PATH bash build.sh
```

Add `debug` as an argument for an unminified build: `bash build.sh debug`.

Files worth editing first:

- `src/zen-ui.coffee`: toolbar, buttons, and labels
- `src/zen-widgets.coffee`: sliders and controls
- `index.html`: page chrome, the footer credit links, and the colour of everything around the canvas
- `src/zen-renderer.coffee`: exposure, ray count, and render behaviour

## Licence

MIT, copyright 2013 Micah Elizabeth Scott. Full text in `LICENSE.txt`. Retain that notice in anything you ship.

## Provenance and caveats

The original upstream repository at `scanlime/zenphoton` no longer resolves. This build came from the `jshaw/zenphoton` fork, last commit June 2018. If you take this past a demo, fork a mirror into your own org so the source does not disappear on you mid-project.

Two things to fix before this becomes a deliverable:

1. The render loop dates from 2013 and predates most modern mobile hardware. Test on the actual target devices early.
2. Touch handling is minimal. Expect real work to make dragging feel right on a phone or a kiosk panel.
