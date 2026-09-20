# AccuCompounder Research — free website MVP

EN showcase, privacy-safe (% + tickers only), 100% free on GitHub Pages.

## Wat is gebouwd
- `index.html` — hero + KPI + benchmark-chart (Portfolio vs URTH/SPY rebased 100) + allocatie donut
- `portfolio.html` — 6 ETFs + 3 stocks uit live JSON, in %
- `pipeline.html` — 2 consolidated advisors (Stock 11 HOLD + ETF 73: 5 BUY / 22 ACCUMULATE)
- `trades.html` + `trades.xml` — SELL/HOLD log + RSS-feed
- `methodology.html` — UCITS-accumulerend + honest reporting + disclaimer
- `tearsheet.html` + `tearsheet-2026-09.pdf` — monthly 1-page PDF (maand-archief `tearsheet-YYYY-MM.pdf`)
- `data/*.json` — holdings/pipeline/trades via `export_site_json.py`, benchmark via `fetch_benchmark.py` (alleen %)
- `404.html` — branded not-found met nav + links (Pages pikt automatisch op)
- `assets/favicon.svg` + `assets/og-image.png` (1200x630) — favicon + link-preview, 100% gratis zelf gegenereerd
- `.github/workflows/deploy.yml` — gratis Pages deploy

## Lokaal testen (gratis)
```bash
cd accucompounder-site
python3 -m http.server 8000
# open http://localhost:8000
```

## Data verversen
```bash
python3 clawd/investment/export_site_json.py
./clawd/investment/.venv/bin/python clawd/investment/fetch_benchmark.py
./clawd/investment/.venv/bin/python clawd/investment/generate_tearsheet.py
```

## Tearsheet routine (maandelijks, SME)
- Begin maand: run `generate_tearsheet.py` → nieuwe `tearsheet-YYYY-MM.pdf`
- `tearsheet.html` toont latest + archive-lijst (zelfde pattern `tearsheet-YYYY-MM.pdf`)
- Nav + footer op alle pagina's uniform: Home / Portfolio / Pipeline / Trades / Methodology / Tearsheet

## Live zetten — 5 min, €0
1. Maak nieuwe public GitHub repo `accucompounder` (gratis account)
2. Upload inhoud van `accucompounder-site/` naar `main` branch
3. GitHub → Settings → Pages → Source: GitHub Actions
4. Push → Actions draait `Deploy to GitHub Pages` → live op `https://guy907.github.io/accucompounder/`
5. Bij elke aan/verkoop: run exporter lokaal, commit `data/*.json`, push → site live in ~1-2 min. Of plan nightly Action.

Geen domeinkosten, geen server, geen API-keys. RSS: `trades.xml`. Tearsheet-archief: `tearsheet-2026-09.pdf` (eerste editie).

## Na livegang — 1x site-URL vervangen (voor mooie previews)
`og:image` staat nu op `https://guy907.github.io/accucompounder/assets/og-image.png`.
Na deploy 1x zoeken-vervangen `guy907` door je GitHub-username in alle `*.html` → X/LinkedIn/WhatsApp tonen dan de navy/emerald kaart. Test via https://cards-dev.twitter.com/validator of https://www.opengraph.xyz/ (beide gratis).
