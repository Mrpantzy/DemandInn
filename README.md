# DemandInn

AI demand forecasting for hotel food and beverage: a landing page plus a live demo app (Hotel Aurora, simulated data).

## Run it locally

Everything is in `index.html` (React, loaded from a CDN, plus all the code and demo data). You can open the file straight in a browser, or start a small local server:

```bash
python3 -m http.server 8000
```

Then go to http://localhost:8000. The demo app is at http://localhost:8000/#/app.

## Deploy

It's a static site, so it works on GitHub Pages, Netlify or Vercel without a build step. Keep the file named `index.html` at the root of the repository.
