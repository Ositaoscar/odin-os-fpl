# ODIN OS — FPL Intelligence Engine

Live FPL dashboard for **Hacunha Mateta** · Trenches PL · Painhub

## Live Dashboard
**[→ Open Dashboard](https://ositaoscar.github.io/odin-os-fpl/)**

Fetches live data directly from the FPL API on every load. No backend required.

## What It Shows
- ⏱ Live deadline countdown
- 📊 VaR audit — per-player risk scores with form weighting
- 🎯 Auto captain pick — scored by `(form×2.0) + (ppg×1.5) + (ict×0.1)`
- 🪑 Optimal bench order — outfield by PPG, GK last
- 🏆 Live league positions — Trenches PL + Painhub
- 💊 Chip signal — TC / BB / FH / WC status
- 🏥 Injury monitor
- 📈 Squad health score — rolling VaR + form analysis
- 📉 VaR trend tracker

## Local Pipeline
```bash
cd odin_os
source env/bin/activate
python run_odin.py        # full pipeline
python dashboard_server.py  # local dashboard on :5001
```

## Files
| File | Purpose |
|---|---|
| `config.py` | Single source of truth — update after every transfer |
| `run_odin.py` | Full pipeline entry point |
| `transfer_suggester.py` | KNN-based transfer recommendations |
| `chip_signal.py` | Consolidated chip advice |
| `auto_select.py` | Captain + bench order recommendations |
| `chip_planner.py` | GW-by-GW chip analysis |
| `bb_optimizer.py` | Bench boost optimizer |
| `index.html` | GitHub Pages dashboard (this file) |
| `dashboard_server.py` | Local Flask server |

## Update Squad
Edit `config.py` after every transfer — `SQUAD`, `STARTING_XI`, `BENCH`, `CHIPS_REMAINING`.  
Push to GitHub → dashboard updates automatically.
