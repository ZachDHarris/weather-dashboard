# Ezee Fiber Network Weather Board

A single-page, wallboard-style weather dashboard for five regions:

| Site | Radar region |
|---|---|
| Houston, TX | Houston Region |
| Albuquerque + Santa Fe, NM | Albuquerque Region |
| Kent, WA + Salem, OR | Pacific Northwest |
| Streamwood + Naperville, IL | Chicago Midwest |
| Novi, MI | Metro Detroit Region |

**Live:** https://zachdharris.github.io/weather-dashboard/

## What's on it

- **Condition tiles** (across the top) — temperature with 1-hour trend, conditions, high/low, wind direction/speed/gusts, humidity, and the highest rain chance over the next 12 hours. Local time is shown with the offset from Central.
- **Radar** — NOAA MRMS quality-controlled base reflectivity (the same mosaic used by radar.weather.gov), refreshed about every 2 minutes. Tiles are smoothed in the browser so storms have clean curved edges instead of the blocky 1 km grid. All five maps animate the last hour together; the radar time on screen is shown in the header. Major roads and highway shields are drawn over the radar for reference.
- **NWS alerts** — active warnings, watches, and advisories for each site. Warning polygons are drawn on the maps; click a tile's alert chip for the full text.

Maps return to their home view 3 minutes after you pan or zoom. Data refreshes on its own, and the page fully reloads every 6 hours so a TV can run it unattended.

**Keyboard:** `Space` play/pause · `←` `→` step frames · `R` refresh · `F` fullscreen

## Data sources (all free, no API keys)

- Radar: [NOAA MRMS](https://www.nssl.noaa.gov/projects/mrms/) via `opengeo.ncep.noaa.gov` WMS
- Conditions/forecast: [Open-Meteo](https://open-meteo.com/)
- Alerts: [api.weather.gov](https://www.weather.gov/documentation/services-web-api)
- Basemap: Esri World Dark Gray Canvas
- Map library: [Leaflet](https://leafletjs.com/)

## Editing sites

Locations live in the `LOCATIONS` array near the top of the script in `index.html`. Each entry has the pin coordinates, IANA time zone, and the `bounds` the map opens to. Extra pins on the same map go in `extra`, and `pinDrop` (pixels) nudges a pin down when it covers the map's own city label.
