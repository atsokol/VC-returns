# VC Returns — Monte Carlo Simulation of Venture Capital Portfolio Returns

Monte Carlo simulations of expected returns for VC portfolios at different stages, built with R and [Quarto](https://quarto.org/).

## Notebooks

### `vc-returns.qmd` — General VC Portfolio Returns

Simulates net MOIC distributions for a 20-deal portfolio across Series A, B, and C stages. Models deal-level outcomes using binned probability distributions with log-uniform sampling within each bucket. Applies Toloka's fee structure (entry fees, processing fees, carry with hurdle rate). Compares return profiles across series.

### `yc-seed-returns.qmd` — YC Seed Returns with Batch Effects

Models returns for seed-stage investments in YC Demo Day funds, incorporating **batch-quality effects** — the observation that some YC batches produce dramatically better outcomes than others (0.53x to 11.63x across 2016–2020 vintages).

Key features:
- **Batch quality model**: log-normal multiplier $q \sim \text{LogNormal}(0, \sigma)$ scales deal-level MOICs per batch
- **Calibration** against AngelList Demo Day Fund actual batch MOICs
- **Diversification analysis**: investing across 1–12 batches (20 deals each) — shows how multi-batch strategies eliminate loss risk while preserving expected returns
- Outputs both HTML and PDF

## Data Sources

- [Jared Heyman / Rebel Fund](https://jaredheyman.medium.com/on-the-176-annual-return-of-a-yc-startup-index-cf4ba8ebef19) — YC unicorn rates, power law returns
- [Lenny's Newsletter / Palle Broe](https://www.lennysnewsletter.com/p/pulling-back-the-curtain-on-the-magic) — YC company outcomes across 4,939 startups
- [AngelList Demo Day Funds](https://www.angellist.com/demo-day-funds) — batch-level net MOICs (2016–2020)

## Requirements

- R ≥ 4.1 with `tidyverse`
- [Quarto](https://quarto.org/) CLI
- LaTeX distribution (e.g. TinyTeX) for PDF output

## Usage

```bash
# Render both HTML and PDF
quarto render yc-seed-returns.qmd

# Render HTML only
quarto render vc-returns.qmd
```

## License

This project is for informational purposes only. Past performance is not a guarantee of future returns.