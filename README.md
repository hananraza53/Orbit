# Orbit — Weather, worldwide

A responsive weather explorer built with Three.js, GSAP and Vite. No API key is required for personal, non-commercial use of Open-Meteo's free endpoint.

## Run locally

Install Node.js 22.12+ (or a newer supported LTS). Open this folder in VS Code or Antigravity, then run:

```sh
npm install
npm run dev
```

Open the localhost URL printed in the terminal. Do not double-click index.html: modules and data requests require a web server.

## Deploy to Vercel

Upload this project to your GitHub repository and import it in Vercel. Choose Vite, build command `npm run build`, output directory `dist`. The included vercel.json supplies these settings. No environment variables are needed.

## Deploy to Netlify

Import the repository. The included netlify.toml sets `npm run build` and `dist`. Alternatively, run `npm run build` and drag the complete dist folder into Netlify Drop. The release ZIP includes a prebuilt dist folder.

## Features

- Textured Three.js globe with country outlines, atmospheric rim, stars, camera flight, zoom, drag and optional automatic rotation.
- Click the Earth for forecast at the selected coordinates. Country matches also open a city browser; boundary data is simplified and does not express a political position.
- Global city search with administrative-region labels and locally bundled country/city browsing.
- Model-based current weather, feels-like temperature, humidity, wind, rain probability, 24-hour temperature chart and seven-day forecasts.
- Click a daily forecast to see sunrise, sunset and maximum UV.
- Celsius/Fahrenheit, geolocation, saved locations, refresh and 15-minute refresh while visible.
- Local storage preserves saved places, selected location and units on this browser only.
- Responsive layout, keyboard controls, reduced-motion support and a fallback for devices without WebGL.

## Data and behavior

Forecasts and city search require internet access to api.open-meteo.com and geocoding-api.open-meteo.com. The UI displays errors and retry controls when data is unavailable; it does not replace real weather with fake values. All forecast times use the selected location's local timezone. Winds use km/h. Rain chance is hourly probability, not measured rainfall. Globe coordinate selections are not reverse-geocoded to city names. Country lists are geographic catalogues; remote places missing from the catalogue can be found through global search or selected on the globe.

Open-Meteo's free API is intended for non-commercial use and subject to its usage limits. For a commercial launch, review https://open-meteo.com/en/pricing and configure a suitable customer endpoint/key via a server-side proxy; do not publish secret keys in frontend code. No severe weather alert service is included.

Geolocation needs HTTPS or localhost and browser permission. Denying permission leaves city search usable. Browsers or privacy settings may prevent local storage. The globe renders at a capped pixel ratio and approximately 30 fps and pauses rendering in hidden tabs; weather remains usable without WebGL. Google Fonts are optional and system font fallbacks are provided.

## Asset attribution

- Forecasts: Open-Meteo, https://open-meteo.com/ (CC BY 4.0 data; attribution is included in the interface).
- City search: GeoNames through Open-Meteo.
- Country/city catalogue: country-state-city npm package (retain its bundled license in node_modules when redistributing dependencies).
- Earth texture: webgl-earth example asset, https://github.com/turban/webgl-earth/blob/master/images/2_no_clouds_4k.jpg (NASA Blue Marble imagery).
- Country outlines: https://github.com/johan/world.geo.json (Natural Earth-derived geographic data).
- Icons: Lucide (ISC). Three.js (MIT); GSAP (standard GSAP license); Vite (MIT).

To regenerate the bundled country/city JSON after updating country-state-city: `node scripts/prepare-data.cjs`.
