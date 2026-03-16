# 🌧️ Wausau Pilot & Review — Weather Radar Widget

A self-contained, embeddable weather radar and forecast tool built for [Wausau Pilot & Review](https://wausaupilotandreview.com/), covering north-central Wisconsin (~90-mile radius around Wausau).

![Widget Preview](https://img.shields.io/badge/status-live-brightgreen) ![License](https://img.shields.io/badge/license-MIT-blue)

## What It Does

- **Live Doppler Radar** — Animated radar loop (last 2 hours, 10-minute frames) using [RainViewer](https://www.rainviewer.com/) tile data overlaid on a Leaflet.js map, centered on Wausau with pan-constrained bounds
- **Playback Controls** — Play/pause, step forward/back, clickable timeline scrubber, auto-plays on load
- **Dual Legend** — Separate color scales for rain (green → red → magenta) and snow (light cyan → deep blue), mapped to RainViewer's Universal Blue color scheme
- **NWS Weather Alerts** — Active alerts for Wisconsin pulled from `api.weather.gov`, with severity tags, county labels, weather emojis, and auto-expand for warnings
- **Current Conditions** — Live temperature, feels-like, humidity, wind speed, and description from the nearest NWS observation station
- **7-Day Forecast** — Full NWS forecast with high/low temps, weather icons, precipitation probability, and click-to-expand detailed forecast text
- **City Selector** — Dropdown to switch between 12 north-central WI cities (Wausau, Stevens Point, Marshfield, Rhinelander, Antigo, Merrill, Minocqua, Medford, Tomahawk, Shawano, Wisconsin Rapids, Plover)
- **Auto-Refresh** — All data (radar, alerts, conditions, forecast) refreshes every 5 minutes, client-side

## Data Sources

| Data | Source | Cost |
|------|--------|------|
| Radar tiles | [RainViewer API](https://www.rainviewer.com/api.html) | Free |
| Forecasts & alerts | [NWS API](https://www.weather.gov/documentation/services-web-api) | Free |
| Current conditions | [NWS Observation Stations](https://www.weather.gov/documentation/services-web-api) | Free |
| Base map | [CartoDB Positron](https://carto.com/basemaps/) via Leaflet.js | Free |

No API keys required. All requests are made client-side from the user's browser.

## Tech Stack

Single HTML file — no build step, no dependencies to install, no server required.

- **Leaflet.js** (via CDN) — interactive map
- **RainViewer Weather Maps API** — radar tile overlay
- **NWS api.weather.gov** — forecasts, alerts, observations
- **Playfair Display + Source Sans 3** (Google Fonts) — typography matching WPR brand
- **Vanilla JavaScript** — no frameworks

## Deployment

This widget is deployed via **GitHub Pages**. Any push to `main` automatically updates the live site.

To deploy your own:

1. Fork or clone this repo
2. Go to **Settings → Pages**
3. Set source to `main` branch, `/ (root)` folder
4. Your live URL will be `https://<username>.github.io/<repo-name>/`

## Embedding on WordPress

**Option A — iframe** (simplest):
```html
<iframe src="https://<username>.github.io/<repo-name>/" 
        width="100%" height="1200" frameborder="0"
        style="max-width:860px; margin:0 auto; display:block;">
</iframe>
```

**Option B — Custom HTML block**:
Copy the full contents of `index.html` into a WordPress Custom HTML block or widget area.

## Customization

Key configuration values are at the top of the `<script>` section:

- `WAUSAU` — center coordinates `[lat, lon]`
- `ZOOM` — default map zoom level (8 ≈ 90-mile radius)
- `BOUNDS` — pan-constrain boundaries
- `CITIES` — array of cities for the forecast dropdown
- `RADAR_OP` — radar overlay opacity (0–1)
- `ANIM_DELAY` — milliseconds between animation frames
- `REFRESH` — auto-refresh interval in milliseconds

## Brand

Styled to match the Wausau Pilot & Review visual identity:

- **Teal** (#4aaba7) primary color from the WPR typewriter logo
- **Playfair Display** serif headers for editorial feel
- **Black borders** and **cream backgrounds** for newspaper aesthetic
- WPR logo embedded inline (base64)

## License

MIT — built for Wausau Pilot & Review by Rowan Flynn.
