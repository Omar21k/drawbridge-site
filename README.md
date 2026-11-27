# DrawBridge website

Landing page for DrawBridge, the VS Code extension that holds AI-written code until you prove you understand it.

Live at **https://drawbridge-lake.vercel.app**

## What's here

| Path | What it is |
| --- | --- |
| `index.html` | The whole page: nav, hero, Product, How it works, Demo, About, Waitlist, footer. Plain HTML, CSS and JS, no build step. |
| `assets/` | Logo, goblin sprites, demo reel, social preview image, favicon. |
| `api/waitlist.js` | Vercel serverless function for the waitlist. `POST` saves a signup, `GET` returns the count. |

## Waitlist storage

Signups are saved in an Upstash for Redis database (`drawbridge-waitlist`) connected through the Vercel Marketplace. Vercel sets `KV_REST_API_URL` and `KV_REST_API_TOKEN` automatically. Never commit them.

- `waitlist:emails` is a set of every email.
- `waitlist:entry:<email>` holds that person's role, school, source and join date.

View them in Vercel → drawbridge → Storage → drawbridge-waitlist → Data Browser.

## Editing and deploying

Every push to `main` deploys to production on Vercel. To preview locally:

```bash
python3 -m http.server 5178
```

The waitlist API only runs on Vercel (or with `npx vercel dev`).
