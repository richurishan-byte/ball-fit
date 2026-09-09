# 🏀 BallFit

**The most useless measurement your car has ever needed.**

BallFit calculates approximately how many balls (footballs, basketballs, tennis balls, and more) can fit inside the cargo space of 200 real car models — built for the **"Useless Things"** hackathon theme.

> 🔗 **Live demo:** _[add your GitHub Pages link here once deployed]_

![BallFit screenshot](docs/screenshot.png)
_(add a screenshot to `docs/screenshot.png` — see below)_

---

## ✨ What it does

1. **Pick a car** — search 200 real vehicles (Toyota Corolla to Rolls-Royce Cullinan) with real boot/cargo volumes.
2. **Pick a ball** — football, basketball, volleyball, tennis ball, baseball, softball, table tennis ball, or rugby ball.
3. **Get an estimate** — a big odometer-style number reveal shows how many balls physically fit, plus a "Uselessness-O-Meter" score.
4. **Compare** — see every ball's count for the same car, or the same ball across two different cars.

Everything is a single static HTML file — no build step, no backend, no dependencies beyond two Google Fonts.

---

## 🧮 The math

```
Usable Space   = Car boot volume (L)          // passenger cabin volume isn't in the dataset,
                                                // so usable space = boot/storage volume only
Ball Volume    = (4/3) × π × (diameter / 2)³   // treated as a sphere, converted cm³ → L
Packing Factor = 0.64                          // random close packing efficiency for spheres
Ball Count     = floor(Usable Space × 0.64 ÷ Ball Volume)
```

The rugby ball isn't spherical, so it uses a fixed reference volume (≈5.7 L) instead of the sphere formula.

This is a **for-fun estimate**, not an engineering measurement — real trunks have wheel wells, shapes, and your cousin's golf bag. The app says so on the results screen.

---

## 🗂️ Data sources

- **Car dataset**: 200 car models with brand, model, seat count, and boot/storage volume (litres).
- **Ball dataset**: standard diameters for 8 common ball types.

Both datasets are embedded directly in `index.html` as JavaScript arrays (`CARS` and `BALLS`) — no external API calls, so the app works fully offline.

---

## 🛠️ Tech stack

- Plain HTML / CSS / JavaScript — zero frameworks, zero build tools
- Google Fonts: `Big Shoulders Display` (headlines) + `IBM Plex Mono` (data readouts)
- Inline SVG for the uselessness gauge
- `requestAnimationFrame` for the odometer count-up animation

---

## 🚀 Run it locally

No install needed — it's one file.

```bash
git clone https://github.com/<your-username>/ballfit.git
cd ballfit
open index.html      # macOS
# or just double-click index.html
```

Or serve it (avoids any browser file:// quirks):

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

---

## 🌐 Deploy to GitHub Pages (for your demo link)

1. Push this repo to GitHub.
2. Go to **Settings → Pages**.
3. Under **Source**, select the `main` branch and `/ (root)` folder.
4. Save — your live URL will appear at `https://<your-username>.github.io/<repo-name>/` within a minute or two.
5. Drop that link into this README and your submission form.

---

## 📁 Project structure

```
ballfit/
├── index.html      # the entire app (HTML + CSS + JS + embedded data)
├── README.md        # this file
├── LICENSE
└── docs/
    └── screenshot.png   # add your own screenshot here
```

---

## 💡 Ideas for "next round" features

- Shareable result cards (canvas export)
- Sound effects on the odometer reveal
- Custom ball diameter input ("mystery ball" mode)
- Session history / mini leaderboard of past calculations
- Confetti at Uselessness scores above 90

---

## 🏆 Built for

`[Hackathon name]` — theme: **Useless Things**, `[event date]`

## 📄 License

MIT — see [LICENSE](LICENSE).
