# outft. DNA detector

Camera-based outfit style DNA analyzer. Take a photo, get an aesthetic breakdown (Quiet luxury / Old money / Scandi / etc.) powered by Claude's vision.

## Setup

```bash
npm install
```

Set your API key — create a `.env` file or export it:
```bash
export ANTHROPIC_API_KEY=sk-ant-...
```

Run locally:
```bash
npm start
# or for auto-reload during dev:
npm run dev
```

Open `http://localhost:3000` on your phone (or use a tunnel — see below).

## Camera on mobile

The camera API requires HTTPS except on `localhost`. If you're testing from your phone on the same network:

```bash
# Install ngrok (one-time)
npm install -g ngrok

# In a second terminal, tunnel to your local server
ngrok http 3000
```

Use the `https://xxxx.ngrok.io` URL on your phone — camera will work over the ngrok HTTPS tunnel.

## Deploy to Render / Railway / Fly.io

All three work with zero config. Example for Railway:

1. Push this folder to a GitHub repo
2. New project on railway.app → Deploy from GitHub repo
3. Add environment variable: `ANTHROPIC_API_KEY=sk-ant-...`
4. Railway auto-detects Node, runs `npm start`, gives you a public HTTPS URL

For Render.com:
- Build command: `npm install`
- Start command: `npm start`
- Add env var: `ANTHROPIC_API_KEY`

## Embed on your website

If you want to embed this in an existing site rather than run it standalone, you have two options:

**Option A — iframe embed** (easiest):
```html
<iframe src="https://your-deployed-url.com" 
  style="width:390px;height:700px;border:none;border-radius:20px">
</iframe>
```

**Option B — use the API endpoint directly** from your own frontend:
```js
const res = await fetch('https://your-deployed-url.com/api/analyze', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ imageBase64: '<base64 jpeg>', mediaType: 'image/jpeg' })
});
const { aesthetics, tags, insight } = await res.json();
```

## File structure

```
outft-dna/
├── server.js          ← Express backend, proxies Anthropic API
├── package.json
├── .env               ← Add this yourself: ANTHROPIC_API_KEY=sk-ant-...
├── README.md
└── public/
    └── index.html     ← Full frontend (camera + results UI)
```

The API key never touches the browser — only `server.js` calls Anthropic.
