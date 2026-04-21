# Bayesian Conditional Beta for Korean ETF Market Regimes

This project estimates time-varying market beta for a Korean equity ETF using Bayesian conditional beta models and a two-regime Markov switching framework. The analysis focuses on whether market uncertainty, proxied by VKOSPI, changes beta exposure and regime transition dynamics.

The main empirical target is TIGER Semiconductor ETF excess returns relative to KOSPI200 excess returns. The workflow compares a static CAPM baseline, rolling-window CAPM, Bayesian conditional beta models with Normal and Student-t errors, and a Markov switching extension with VKOSPI-dependent transition probabilities.

## Research Question

Does market uncertainty affect the conditional beta of a Korean sector ETF, and does VKOSPI help explain transitions between calm and crisis regimes?

## Methodology

- Static CAPM for a fixed-beta baseline
- Rolling-window CAPM for frequentist time-varying beta estimates
- Bayesian conditional beta model with Normal errors
- Bayesian conditional beta model with Student-t errors
- Two-regime Bayesian Markov switching model
- VKOSPI-standardized transition equation for regime dynamics
- MCMC posterior sampling and posterior interval analysis

## Key Results

The Markov switching model separates the sample into low-uncertainty and high-uncertainty regimes:

- Low-uncertainty regime market beta: `1.1176` with 95% interval `[1.0863, 1.1501]`
- High-uncertainty regime market beta: `0.8741` with 95% interval `[0.7736, 0.9695]`
- Low-uncertainty regime volatility: `0.011352`
- High-uncertainty regime volatility: `0.025585`
- VKOSPI effect on high-uncertainty persistence: `1.1758` with 95% interval `[0.4446, 1.9070]`

These results suggest that ETF market exposure and volatility differ materially across regimes, and that higher VKOSPI is associated with stronger persistence of the high-uncertainty regime.

## Repository Structure

```text
.
|-- notebooks/
|   |-- Bayesian_Conditional_Beta_MS.ipynb
|   `-- Bayesian_Results_Analysis.ipynb
|-- paper/
|   `-- Bayesian_Conditional_Beta_Term_Paper.pdf
|-- results/
|   |-- figures/
|   |   |-- Figure1_Regime_Probability.png
|   |   |-- Figure2_Transition_Probability_VKOSPI_Revised.png
|   |   `-- Figure3_Regime_Return_Distributions.png
|   `-- tables/
|       |-- Table1_Regime_Parameters.csv
|       `-- Table2_Transition_Effects_Revised.csv
|-- README.md
`-- requirements.txt
```

## Main Files

- `notebooks/Bayesian_Conditional_Beta_MS.ipynb`: main end-to-end notebook for data loading, model estimation, MCMC sampling, regime analysis, and result export.
- `notebooks/Bayesian_Results_Analysis.ipynb`: supplementary notebook for regenerating figures and summary analysis from saved result CSV files.
- `paper/Bayesian_Conditional_Beta_Term_Paper.pdf`: final write-up of the methodology and empirical findings.
- `results/figures/`: exported figures used for reporting.
- `results/tables/`: compact result tables for regime parameters and transition effects.

## Data Availability

Raw market data is excluded from this repository because of data licensing and redistribution constraints.

To rerun the main notebook, prepare a merged data file with the following expected path:

```text
Data/merged_data.csv
```

The notebook expects columns for dates, KODEX ETF excess returns, KOSPI200 excess returns, and VKOSPI. If you prefer a lowercase folder convention, update the notebook path from `Data/merged_data.csv` to `data/merged_data.csv`.

## How to Run

Create a Python environment and install dependencies:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

Then open the main notebook:

```powershell
jupyter notebook notebooks/Bayesian_Conditional_Beta_MS.ipynb
```

For result-only analysis, open:

```powershell
jupyter notebook notebooks/Bayesian_Results_Analysis.ipynb
```

## Outputs

The repository includes selected final outputs:

- Regime probability plot: `results/figures/Figure1_Regime_Probability.png`
- VKOSPI transition probability plot: `results/figures/Figure2_Transition_Probability_VKOSPI_Revised.png`
- Regime return distribution plot: `results/figures/Figure3_Regime_Return_Distributions.png`
- Regime parameter table: `results/tables/Table1_Regime_Parameters.csv`
- Transition effect table: `results/tables/Table2_Transition_Effects_Revised.csv`

## Notes

This project was developed as a Bayesian macro-finance and machine learning research assignment. The public repository is curated as a portfolio version, so raw data files and literature PDFs are intentionally excluded.
