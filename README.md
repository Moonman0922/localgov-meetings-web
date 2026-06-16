# localgov-meetings-web

**Hosted front-end for [localgov-meetings](https://github.com/Moonman0922/localgov-meetings)** —
a single static page that lets anyone enter a U.S. address and get a calendar (`.ics`) of
their local government meetings (council / board / commission), with agendas.

This repo is **only the UI** (one `index.html`), so it can be published free on **GitHub
Pages**. All the actual work — geocoding, fetching meetings from the Legistar civic API
and iCal feeds, optional AI search — happens in the **backend** (`server.py` in the main
repo), because the Census and Legistar APIs don't allow direct browser calls.

## Use it

1. **Deploy the backend** (`server.py` from the
   [localgov-meetings](https://github.com/Moonman0922/localgov-meetings) repo) on any
   Python host (Render, Fly.io, Replit, Railway, a VPS). You get a URL like
   `https://your-backend.example.com`.
2. **Open this site with that backend:**
   ```
   https://<your-pages-url>/?api=https://your-backend.example.com
   ```
   The backend URL is remembered (localStorage), so you only pass `?api=` once. You can
   also click **set it now** on the page.

That's it — type an address, pick a method (official sources / auto / AI), and download
the `.ics` or add events straight to Google Calendar.

## Embed it

```html
<iframe src="https://<your-pages-url>/?embed=1&api=https://your-backend.example.com"
        width="100%" height="640" style="border:0"></iframe>
```

## Why split into two repos

- This repo is **public** so GitHub Pages can serve it.
- The engine, meeting registry, and server logic live in the **private** main repo.
- The page is a thin client of the backend's open API (`/api/meetings`), so you can also
  build your own front-end against the same API.

> Not legal advice. Meeting times change — confirm against the official source.

## License

MIT.
