# outft.

A mobile-first outfit journal with camera capture and AI-powered style DNA analysis. This project combines the full outft. product prototype with the working DNA analyzer in one deployable Node application.

Live at: https://outft-dna-production.up.railway.app

## Run locally

Requirements: Node.js 20 or newer and an Anthropic API key.

```bash
npm install
cp .env.example .env
```

Put your key in `.env`, then run:

```bash
npm run dev
```

Open `http://localhost:3000`. The browser camera works on localhost. On a phone, use an HTTPS tunnel or deploy the app first.

## What works

- Responsive mobile product prototype
- Rear and front camera capture
- Photo upload fallback
- Server-side Anthropic vision request
- Style DNA percentages, tags, and insight
- Persistent local product state for traces, follows, messages, collections, profile, and premium demo access
- Latest captured outfit synchronized across Home, Profile, and Fashion DNA
- Demo sign-in with email, Apple, or guest mode
- Home and Friends’ Traces as a connected two-tab destination
- Portrait 3:4 capture presented as a polaroid-style barcode receipt
- DNA-first Twins view and priced Premium reminder in Activity
- Image-first friend traces integrated directly into Home with visible comments
- Persistent Camera navigation that remains reachable after saving a receipt
- Circular DNA summary and Wrapped entry on Twins
- Numbered polaroid treatment for Saves and Backlog
- Installable PWA metadata
- API health endpoint at `/api/health`

The app is now a fully connected local product demo. Seed feed content remains illustrative, while new traces, follows, messages, collection saves, profile edits, and premium demo access persist in the browser. Replace the local adapter with Supabase and StoreKit before production launch.

## Deploy

Deploy the repository to Railway, Render, or Fly.io.

- Build command: `npm install`
- Start command: `npm start`
- Environment variable: `ANTHROPIC_API_KEY`
- Health check: `/api/health`

Never expose the Anthropic key in browser code.

## Next production milestone

Add Supabase authentication, Postgres tables, and Storage for user-uploaded outfit photos. Then connect the current prototype screens to persisted data before wrapping the PWA with Capacitor for the App Store and Google Play.
