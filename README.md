# Adwaita Icon Theme legacy

A fullcolor icon theme providing fallback for legacy apps. See [the issue](https://gitlab.gnome.org/GNOME/adwaita-icon-theme/-/issues/288) for more info.

### Cursor generation

Cursors are in the xcursorgen format. They come in multiple sizes and possibly animation frames per file. Generating them is a two sstep process.

First step is to render the source svg into multiple pngs. This is done with the `renderpngs.py` script. It takes the adwaita.svg file and generates the pngs for the different sizes and saves them in the `pngs/` directory.

The cursors are then generated using the `cursorgen.py` script. The `cursors.py` file contains a dictionary that maps the cursor name to the *cursor info* files such as `pngs/default.in`. The *cursor info* is a dictionary that contains the hotspot, frames, and duration. If the cursor is animated, the duration is the milliseconds each frame takes.

Coordinates of the hotspots are only specified for the nominal 24x24 size. The script scales the coordinates to the different sizes and generates the cursors for the different sizes.

The `cursorgen.py` script generates the cursors for the different sizes and saves them in the `AdwaitaLegacy/cursors/` directory.