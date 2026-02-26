# AxisForge AI — Intelligent CNC Machining Platform

> Upload STEP / IGES 3D part files and generate production-ready G-code & M-code  
> for wood, stone, and composite CNC machines — fully powered by Claude AI.

---

## Features

- **AI-Powered Analysis** — Detects features, complexity, axes required, bounding box, surface area
- **11 Materials** — Solid wood, plywood/MDF, hardwoods, granite, marble, sandstone, carbon fiber, fiberglass, G10, HDPE, aluminium composite
- **12 CNC Machines** — Haas, Fanuc, Mazak, DMG Mori, Biesse, Homag, MultiCam, Thermwood, Laguna, ShopBot, Onsrud
- **Autonomous G/M Code** — Roughing, finishing, tool changes, 5-axis contouring, drilling cycles
- **Controller Dialects** — Haas NGC, Fanuc 0i/31i, Heidenhain iTNC 640, Mazatrol SmoothX, and more
- **One-click `.nc` download** — Ready to load directly onto any compatible CNC controller

---

## Tech Stack

| Layer      | Technology              |
|------------|-------------------------|
| Frontend   | React 18 + Vite 5       |
| AI Engine  | Anthropic Claude API    |
| Styling    | Inline CSS (zero deps)  |
| Fonts      | JetBrains Mono + Bebas Neue (Google Fonts) |
| Deploy     | Vercel (SPA)            |

---

## Local Development

```bash
# 1. Clone the repo
git clone https://github.com/YOUR_USERNAME/axisforge-ai.git
cd axisforge-ai

# 2. Install dependencies
npm install

# 3. Start dev server
npm run dev
# → http://localhost:3000
```

---

## Deploy to Vercel

### Option A — Vercel CLI
```bash
npm install -g vercel
vercel
```

### Option B — Vercel Dashboard (recommended)
1. Push this repo to GitHub
2. Go to [vercel.com](https://vercel.com) → **Add New Project**
3. Import your GitHub repo
4. Framework preset: **Vite**
5. Build command: `npm run build`
6. Output directory: `dist`
7. Click **Deploy** ✅

> No environment variables required — the Anthropic API key is handled  
> via the Claude.ai artifact proxy when running inside the platform.  
> For standalone deployment outside Claude.ai, add `VITE_ANTHROPIC_API_KEY`  
> to Vercel environment variables and update the fetch headers accordingly.

---

## Project Structure

```
axisforge-ai/
├── index.html          ← Vite entry point + loading splash
├── vite.config.js      ← Vite + React plugin config
├── vercel.json         ← SPA rewrite rules + cache headers
├── package.json
├── .gitignore
├── public/
│   └── favicon.svg
└── src/
    ├── main.jsx        ← React DOM root
    └── App.jsx         ← Full platform (upload → analyse → configure → G-code → export)
```

---

## Adding Your Own Machines

In `src/App.jsx`, add an entry to the `CNC_MACHINES` array:

```js
{ id: "my_machine", name: "My Machine Name", axes: 3, controller: "Fanuc 0i", vendor: "Brand" }
```

---

## License

MIT — free to use, modify, and deploy.
