# Ambulance Fleet Planner

Plan ambulance base locations around one or more hospitals and see coverage, response time and turnaround (TAT) update live as you drag units on the map.

It is a static web app: one `index.html`, no build step, no server code, no API keys.

## Deploy (GitHub → Vercel)

1. **GitHub:** create a new repository (private is fine), click **Add file → Upload files → choose your files**, press **Ctrl+A** (Cmd+A on Mac) to select every file in this folder, and commit. All files sit in one folder, so nothing gets left behind.
2. **Vercel:** go to vercel.com → **Add New → Project** → import the repository.
   - Framework preset: **Other**
   - Build command: leave empty
   - Output directory: leave empty (root)
   - Click **Deploy**.
3. Open the `https://…vercel.app` link. Every push to GitHub redeploys automatically.

## Install it as an app

- **Laptop (Chrome / Edge):** open the Vercel link → click the install icon in the address bar, or menu → *Install Fleet Planner*.
- **Android (Chrome):** menu → *Add to Home screen* / *Install app*.
- **iPhone (Safari):** Share → *Add to Home Screen*.

It then opens in its own window with its own icon. The app itself works offline; the map tiles and place search need internet.

## Where data is stored

- Layouts autosave in each user's own browser (localStorage).
- **Save scenario** downloads a `.json` file; **Load scenario** opens one. Share files to share layouts.
- No database is needed for this. A Supabase backend is only needed if several people must edit the *same* scenarios live.

## Map tiles

Default base map is Esri (works on any domain, no key). OpenStreetMap community styles are also available in *Map & scenario → Base map*. For heavy or public use, check the tile provider's terms of use.

## Files

| Path | Purpose |
|---|---|
| `index.html` | The whole app (UI + logic) |
| `leaflet.js`, `leaflet.css` | Leaflet 1.9.4 map library, bundled locally (BSD-2 licence, see `leaflet-LICENSE.txt`) |
| `manifest.webmanifest`, `icon*.png`, `icon.svg`, `apple-touch-icon.png` | Makes it installable as an app |
| `sw.js` | Caches the app for instant/offline start |
| `vercel.json` | Headers for the service worker and manifest |
