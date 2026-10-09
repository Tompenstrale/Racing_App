# RacingApp 🏁

A complete management tool for drag racing vehicles – vehicle data, parts tracking, run logging and weather-based performance prediction. Single HTML file, no installation, works on any phone or desktop browser.

## Features

### 🔧 Garage
- **Vehicle data card** – SFI tag number, chassis number, make/model, race class, transponder ID, inspection/insurance dates with automatic expiry warnings
- **Multiple vehicles** – switch between vehicles, each with complete data
- **Sections** (engine, transmission, rear axle & final drive, 4-link suspension):
  - Component specs, measurements and tolerances with automatic IN TOLERANCE / OUT OF TOLERANCE status
  - Baseline settings grouped by section (bottom end, cylinder head, intake, exhaust, boost, ignition, clutch, bearings, bars & placement, etc.)
  - Traffic-light status per section visible at a glance
- **Installed parts registry** – run counters per part with replacement intervals (per runs or days), traffic-light status, service history, and a dashboard that flags anything within 20 runs of its interval before the next race weekend
- **Tracked settings** – key/value settings (tire pressure, launch RPM, ...) with full change history: when it changed, the old value, the new value and the source (app / run log / prediction)

### ⏱ Runs
- **Individual run logging** – date, time, track, 60-ft, 1/8 ET, 1/4 ET, trap speed
- **Automatic weather** – fetches current temperature, wind, wind direction and humidity for the selected track (Open-Meteo, no API key needed)
- **Headwind/tailwind** – each track has its start-to-finish direction (bearing); the app calculates wind component along the track
- **Settings snapshot** – every run saves the vehicle settings at the time of the run
- **Prediction flag** – mark runs as representative or exclude them (spin, aborted run, etc.); only included runs affect calculations
- **Edit & delete** – full editing of previously saved runs
- **Bulk logging** – count-only days for parts wear without times

### 📊 Prediction
- **ET prediction in current weather** – estimated 1/4 mile ET right now, based on your included runs, adjusted for temperature and head/tailwind
- **Track-based** – weather is fetched for the selected track (Tierp Arena, Sundsvall Raceway, Mantorp Park, Malmö Raceway), not your GPS position
- **Setting recommendations** – suggested values for tracked settings with one-click apply
- **Public API** – `window.RacingBilen` object with `listVehicles()`, `getSettings()`, `getSetting()`, `updateSetting()` for future integrations

### 📦 Data & Backup
- All data stored locally in the browser (localStorage), per vehicle
- **Backup / Restore** – export everything as a JSON file, restore on any device
- Demo data included – click "Load example" to explore

## Getting started

1. Download `index.html` from this repository (Code → Download ZIP, or open the file directly)
2. Open it in Chrome (or any modern browser)
3. The app starts in the **Prediction** view – switch to **Garage** to create your own vehicle (or explore the demo vehicle first)
4. Log your runs, add your parts, and the prediction improves with every run

Weather fetching requires internet connection; everything else works offline.

## Track registry

Tracks are defined in the `TRACKS` array with latitude, longitude and the start-to-finish bearing (degrees, 0 = north). Adjust bearings to match the real direction of each track for accurate head/tailwind calculations, and add more tracks as needed:

```javascript
const TRACKS = [
  { name: "Tierp Arena", lat: 59.87, lon: 17.51, bearing: 15 },
  ...
];
```

## Tech

Single self-contained HTML file – HTML, CSS and vanilla JavaScript with no dependencies or build step. Open it and it runs.
