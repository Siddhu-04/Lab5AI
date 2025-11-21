# HMM Financial Time Series Analysis with Gaussian Hidden Markov Models

## Overview
This repository contains the complete implementation and analysis for a lab assignment on modeling hidden market regimes in financial time series using Gaussian Hidden Markov Models (HMMs). We analyze daily log returns of the S&P 500 index (^GSPC) from 2015-01-01 to 2025-11-22, identifying low- and high-volatility regimes. The project includes data preprocessing, model fitting, inference, evaluation, and a bonus 3-state extension with AAPL comparison.

The report is formatted as an IEEE conference paper in LaTeX, serving as a tutorial-style explanation. All code is in a Jupyter notebook for reproducibility.

### Key Features
- **Data Source**: Yahoo Finance via `yfinance`.
- **Modeling**: Gaussian HMM with `hmmlearn` (2 states core; 3 states bonus).
- **Insights**: Regime persistence (98.6% low-to-low), forecasting (next state: low vol, 98.6% prob).
- **Visualizations**: Plots of returns, states, prices, and transitions.

## Dependencies
- Python 3.10+
- Libraries: `yfinance`, `hmmlearn`, `pandas`, `numpy`, `matplotlib`, `seaborn`

Install via:
```bash
pip install yfinance hmmlearn pandas numpy matplotlib seaborn
```

## Repository Structure
```
hmm_financial_lab/
├── analysis.ipynb          # Main Jupyter notebook with all code and outputs
├── sp500_log_returns.csv   # Preprocessed S&P 500 log returns
├── returns_plot.png        # Plot: Daily log returns
├── states_over_time.png    # Plot: Inferred states on returns
├── prices_states_eval.png  # Plot: Prices and returns with regimes
├── bonus_3states.png       # Plot: 3-state bonus regimes
├── report.tex              # LaTeX source for IEEE report
├── report.pdf              # Compiled PDF report (generate via pdflatex)
├── README.md               # This file
└── references.bib          # BibTeX for citations (optional)
```

## Quick Start
1. **Clone/Setup**:
   ```bash
   git clone <your-repo-url>
   cd hmm_financial_lab
   ```

2. **Run the Notebook**:
   - Open Jupyter: `jupyter notebook analysis.ipynb`
   - Execute cells sequentially (imports first, then Part 1 → Bonus).
   - Outputs: CSVs, plots, and console prints (e.g., params, transitions).

3. **Generate Report**:
   - Ensure PNGs are in the root.
   - Compile: `pdflatex report.tex` (run twice for refs).
   - Customize: Edit `report.tex` with your names/emails.

## Usage Notes
- **Data Download**: Runs automatically; handles yfinance's auto-adjust (uses 'Close' column).
- **Model Fitting**: EM converges in ~100 iterations; random_state=42 for reproducibility.
- **Evaluation**: Log-likelihood (2-state: 8977.16); compare states via BIC/AIC in notebook.
- **Bonus**: 3-state model and AAPL comparison included—extend for more assets.
- **Customization**: Change `ticker` for other symbols; adjust `n_states` for experiments.

## Results Summary
- **Data**: 2739 log returns (mean: 0.000426, std: 0.011349).
- **2-State HMM**:
  - Low Vol (State 0): μ=0.001003, σ²=0.000051.
  - High Vol (State 1): μ=-0.001603, σ²=0.000430.
  - Transitions: High persistence (0.986 low-to-low).
- **Prediction**: Next regime likely low volatility (98.6% prob).
- **Bonus (AAPL)**: Higher vols [0.000175, 0.001538] vs. S&P.

See `report.pdf` for detailed tutorial, tables, and figures.

## Authors
- Soham Naukudkar (202351135@iiitvadodara.ac.in)
- Siddhikesh Gavit (202351040@iiitvadodara.ac.in)
- Shreyash Borkar (202351132@iiitvadodara.ac.in)

Department of Computer Science and Engineering,  
Indian Institute of Information Technology, Vadodara.

## License
MIT License – feel free to use/modify for educational purposes. Cite the report if reused.

## Acknowledgments
Built with Jupyter, yfinance, and hmmlearn. Inspired by financial regime-switching literature (e.g., Rabiner's HMM tutorial). 

For issues: Open a GitHub issue or email the authors.
