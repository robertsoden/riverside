# Riverside Park map

An interactive map of Riverside Park, Manhattan, from West 59th to West 158th Street. It shows shaded relief and individual trees from the 2017 NYC LiDAR survey, paths, steps, retaining walls, playgrounds, monuments and other park features. The map is fixed to the Manhattan street grid.

It is a static site: `index.html` plus data, glyph, icon and library files. There is no build step and no server code.

## Run locally

```sh
cd riverside-park
python3 -m http.server 8000
# open http://localhost:8000
```

(Opening `index.html` straight from disk won't work; the map loads its data over HTTP.)

## Publish on GitHub Pages

1. Create an empty repository on GitHub (for example `riverside-park`). Don't add a README or licence.
2. From this folder:
   ```sh
   git remote add origin https://github.com/<your-username>/riverside-park.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch: `main`, folder `/ (root)` → Save.**
4. After a minute or two the map is live at `https://<your-username>.github.io/riverside-park/`.

`.nojekyll` tells GitHub Pages to serve the files as they are.

## Tips
- Add `#spring` to the URL to preview the Cherry Walk blossom outside its season (it shows automatically from 25 March to 15 May).
- Relief and trees load in five sections along the park as you pan.

## Contents
| Path | What |
|---|---|
| `index.html` | the page, map style and interface |
| `lib/` | MapLibre GL JS 4.7.1 (BSD-3-Clause) |
| `data/*.geojson`, `data/*.json` | map layers, places list, section index |
| `data/relief_<section>_<azimuth>.webp` | shaded relief, 5 sections × 2 lightings (344° portrait, 254° landscape) |
| `data/trees_<section>_<azimuth>.webp` | LiDAR tree crowns with shadows, same layout |
| `fonts/<Font>/<range>.pbf` | map-label glyphs generated from Fira Sans and Source Serif 4 |
| `icons/` | map symbols (SVG masters and 2× PNGs) |

## Data sources and credits
- **OpenStreetMap:** paths, steps, buildings, roads, piers, amenities and names. © OpenStreetMap contributors, available under the Open Database License (ODbL): https://www.openstreetmap.org/copyright. The map shows this credit in its corner.
- **NYC Open Data, 2017 Topobathymetric LiDAR:** relief and tree crowns derived from the classified point cloud.
- **NYC Open Data, NYC Parks:** Parks Properties (park boundaries: Riverside Park South M353, Riverside Park M071 and M072, clipped to the shoreline for display) and Dog Runs.
- **NYC Open Data, NYC Planimetric Database:** retaining walls.
- **Fonts:** Fira Sans and Source Serif 4, SIL Open Font License 1.1 (licence texts in `fonts/`). Page UI fonts load from Google Fonts.

Amenity data comes from OpenStreetMap and is incomplete. It has not been checked on the ground.
