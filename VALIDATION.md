# Validation

- Vite production build passed.
- Live Open-Meteo request returned current conditions, 168 hourly records and seven daily records; Asia/Karachi timezone verified.
- Live geocoding request distinguished London in the UK, Canada and USA.
- Chromium desktop (1440px) and mobile (390px): no uncaught JavaScript errors and no horizontal page overflow.
- Country picker, city filtering, Lahore selection, bookmarks, unit switch and expandable daily details exercised.
- Direct browser API access was blocked in the build environment. Forecast rendering was tested using the independently downloaded live response intercepted by the test harness. No test interception or sample weather is shipped in the app.
- Earth texture, country boundaries and responsive layouts visually inspected.
- Vercel/Netlify configuration and production files included. Not deployed to a hosting account in this session.
