# THE SPACE + ORBIT

Files (all in the repository root):
- `index.html` — THE SPACE homepage (floating ORBIT icon bottom-right, "Ask ORBIT" buttons speak the greeting)
- `ORBIT.html` — ORBIT workspace. **Everything is inside this one file** (no other script needed)
- `orbit-worker.js` — OPTIONAL live-AI proxy (Cloudflare Worker)
- `README.md`

## ORBIT works immediately on GitHub Pages
ORBIT has a built-in engineering knowledge engine (circuits, electronics, embedded, programming, projects, careers, etc.), so chat, shortcuts, voice input, spoken answers, copy, themes and new chat all work with no server.

## Optional: connect a live AI (can be done from a phone browser)
1. Create a free Cloudflare account, then Workers & Pages > Create > Worker. Paste `orbit-worker.js` and deploy.
2. In the Worker's Settings > Variables: add secret `ANTHROPIC_API_KEY` and variable `ALLOWED_ORIGIN` (your site, e.g. `https://yourname.github.io`).
3. In `ORBIT.html`, find `var ORBIT_API = "";` near the top of the script and paste your Worker URL between the quotes. Commit.
Never paste the API key into any HTML file or commit it to GitHub.

## Notes
- Voice input needs HTTPS (GitHub Pages is HTTPS) and microphone permission; use Chrome or Safari.
- The greeting voice is the phone's built-in text-to-speech set to its lowest pitch and slow speed. Browsers cannot load custom voices, so how deep it sounds depends on the phone's installed voices.
