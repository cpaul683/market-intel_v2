# CEE FAC Market Intelligence Briefing

A personal market intelligence tool for CEE facultative reinsurance underwriting. Runs as a PWA — installable to your phone or desktop home screen. Generates structured briefings via the Anthropic API based on your specified cedants, risk topics, and renewal focus.

## Features

- Configurable briefing form: cedants / markets, risk topic tags, free-text custom instruction
- Six output sections: CEE macro outlook, nat cat / loss environment, pricing & capacity, regulatory developments, cedant intelligence, talking points & actions
- Live streaming output — briefing transmits word by word
- History tab — last 20 briefings saved locally, reloadable at any time
- Copy to clipboard for pasting into email or Word
- Fully offline-capable after first load (briefing generation requires internet)
- Dark mode only

## Files

| File | Purpose |
|---|---|
| `index.html` | The entire application — single self-contained file |
| `manifest.json` | PWA manifest for home screen install |
| `sw.js` | Service worker for offline caching |
| `icon-192.png` | App icon (home screen, small) |
| `icon-512.png` | App icon (home screen, large / splash) |

## Setup

### 1. Deploy to GitHub Pages

1. Create a new GitHub repository (e.g. `market-intel`)
2. Upload all five files to the root of the `main` branch
3. Go to **Settings → Pages**, set source to `main` branch, root folder
4. Your app will be live at `https://YOUR_USERNAME.github.io/market-intel/`

### 2. Add to home screen (iOS)

1. Open your GitHub Pages URL in **Safari**
2. Tap the **Share** button → **Add to Home Screen**
3. Name it "MIB" or "Market Intel" → **Add**

Opens fullscreen with no browser chrome.

### 3. Add your Anthropic API key

1. Open the app → tap **Key** tab (or the KEY button in the header)
2. Paste your key (`sk-ant-...`) and tap **Save Key**
3. The key is stored in `localStorage` on your device only — it is never logged or sent anywhere except the Anthropic API

Get a key at [console.anthropic.com](https://console.anthropic.com).

> **Cost**: Each briefing makes one streaming API call to `claude-sonnet-4-6` with up to 2,000 output tokens. At current Sonnet pricing, a typical briefing costs roughly $0.01–0.02.

## Usage

1. **Briefing tab** — enter cedants or markets (comma-separated), toggle relevant risk topic tags, add any custom instruction or renewal context, adjust which output sections you want, then tap **Generate Briefing**
2. **Output tab** — briefing streams in live; tap **COPY** to copy the full markdown text
3. **History tab** — all previous briefings are saved; tap any card to reload it in the Output tab
4. **Key tab** — manage your API key at any time

## Important caveats

Briefings are generated from the model's training knowledge and general analytical capability — they are **not** pulling live data from NMG, Insuramore, Advisen, or any other proprietary source. Treat outputs as AI-assisted synthesis and analytical framing, not as primary market data. Always verify specific claims against authoritative sources before using in client-facing or underwriting contexts.

## Data & Privacy

- All data (history, API key) is stored in `localStorage` on your device only
- No analytics, no backend, no external services except the Anthropic API
- Your API key is stored in plain `localStorage` — treat device access accordingly

## Updating

Replace `index.html` in the GitHub repo to update the app logic. To force the service worker to pick up the new version, increment the cache version string in `sw.js`: change `'mib-v1'` to `'mib-v2'` before pushing.
