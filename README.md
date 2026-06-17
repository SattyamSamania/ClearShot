# ClearShot

A free, no-signup, in-browser image editor: erase text/watermarks, crop, and remove backgrounds. Nothing is uploaded to a server, everything runs on the visitor's device.

## What it does
- **Erase brush** — paint over text, stickers, or watermarks. Instead of smearing a flat blended color, it reconstructs the real background texture underneath by copying matching patches from nearby unmasked areas of the image (a patch-based content-aware fill, similar in spirit to Photoshop's pre-AI "Content-Aware Fill"). Works on solid colors, gradients, patterns, and busy photo backgrounds.
- **Crop** — drag-select and crop
- **Remove background** — one click, runs a small AI model entirely in the browser (no API key, no signup)
- **Download** — saves the result as a PNG

## Run locally
This is a single static HTML file. No build step.

```
npx serve .
```
or just open `index.html` directly in a browser.

## Deploy to Vercel

**Option A — Vercel CLI**
```
npm i -g vercel
vercel
```
Follow the prompts (link/create a project, accept defaults). It's a static site, so no build command is needed.

**Option B — Vercel dashboard (no CLI)**
1. Push this folder to a GitHub repo (or use Vercel's "drag and drop" deploy at vercel.com/new).
2. Import the repo in the Vercel dashboard.
3. Framework preset: "Other" / static — leave build command empty, output directory `.`.
4. Deploy.

You'll get a `https://your-project.vercel.app` link to send directly.

## Notes
- Background removal downloads a small AI model from a CDN the first time it's used per device (~10–20s), then it's cached by the browser. It needs an internet connection for that first run only.
- Works on mobile browsers too (touch support included for the erase brush).
