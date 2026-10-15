# Island Rail Planner — deployment

A static website: no build step, no database, no server-side code.

```
index.html        the app (map, simulation, editor, overlays; all data embedded)
favicon.svg
fonts/            self-hosted web fonts (SIL Open Font License, see LICENSE-*.txt)
.htaccess         optional Apache compression/caching rules
```

## Deploy

Upload the contents of this folder to any web server or static host, keeping
`fonts/` next to `index.html`. It works at a domain root or in a subfolder
(e.g. `https://example.org/rail/`).

- **Apache / cPanel / shared hosting:** upload via FTP or the file manager into
  `public_html/` (or a subfolder). `.htaccess` is picked up automatically.
- **Nginx:** copy to e.g. `/var/www/rail` and add:
  ```nginx
  location /rail/ {
      alias /var/www/rail/;
      gzip on; gzip_types text/html text/css image/svg+xml;
      location ~* \.woff2$ { expires 1y; }
  }
  ```
- **Netlify / Cloudflare Pages / GitHub Pages:** drag-and-drop or push this
  folder as the site root. No build command; publish directory is the folder itself.
- **WordPress:** upload the folder via SFTP alongside the site (not through the
  media library) and link to it, or embed it in a page with
  `<iframe src="/rail/" style="width:100%;height:85vh;border:0"></iframe>`.

Opening `index.html` directly from disk also works for local previews.

## Notes

- `index.html` is ~1.3 MB uncompressed (terrain, contours, OSM geometry and
  traffic counts are embedded); with gzip enabled it transfers at roughly 0.7 MB.
- Train plans edited in the app are saved in the visitor's own browser
  (localStorage) and can be shared with Export / Import on the Plan tab.
- No external requests are made: no CDN, no analytics, no tracking.

## Data credits

Map data © OpenStreetMap contributors (ODbL). Terrain: Mapzen/AWS Terrain Tiles.
Coastline: Natural Earth / geo-maps. Population: Statistics Canada, 2021 Census.
Traffic: BC Ministry of Transportation and Transit, Traffic Data Program (Open
Government Licence – British Columbia). Timetable: Island Corridor Foundation
potential weekday passenger schedule.
