# American Options Pricing

Numerical methods for pricing American options using Binomial Trees and Least Squares Monte Carlo (LSMC).

## About

This repository demonstrates the valuation of American options, which can be exercised anytime before expiration. Two standard numerical methods are implemented and compared:

- **Binomial Tree Model** - Backward induction with optimal exercise decisions
- **LSMC (Least Squares Monte Carlo)** - Simulation-based pricing using regression

American options exhibit an **early exercise premium** over European options, particularly valuable for puts on dividend-paying stocks.

## Features

- ✅ Vectorized binomial tree (25x speedup over nested loops)
- ✅ LSMC with polynomial regression for continuation value estimation
- ✅ Early exercise boundary visualization
- ✅ Monte Carlo path simulations
- ✅ Multi-asset extension showing LSMC scalability

## Results

Pricing an American put (S₀=100, K=100, T=1yr, r=5%, q=3%, σ=20%):

| Method | Price | Error vs Binomial |
|--------|-------|-------------------|
| Binomial Tree (N=100) | $6.9621 | - |
| LSMC (10k paths) | $6.9814 | 0.3% |
| European Put | $6.7117 | - |

**Early Exercise Premium:** $0.25 (~3.6% of option value)

## Installation
```bash
git clone https://github.com/yourusername/stochastic-processes.git
cd stochastic-processes/understanding_bm
pip install numpy matplotlib pandas jupyter
```

## Usage
```bash
jupyter notebook
```

**Notebooks:**
- `binomial_model_american.ipynb` - Tree-based pricing with vectorization
- `american_options.ipynb` - Complete LSMC implementation
- `binomial_european.ipynb` - European option baseline
- `gbm.ipynb` - Geometric Brownian Motion foundations
- `stoch_processes.ipynb` - Stochastic process simulations
- `mc_stock_portfolio.ipynb` - Portfolio-level Monte Carlo

### Quick Start
```python
# Binomial Tree
price = american_fast_tree(
    K=100, T=1.0, S0=100, r=0.05, 
    N=100, u=1.1, d=0.909, optype='P'
)

# LSMC
price, paths = lsmc_american_put(
    S0=100, K=100, T=1.0, r=0.05, q=0.03, 
    sigma=0.20, N_steps=50, N_paths=10000
)
```

## Project Structure
```
understanding_bm/
├── gbm.ipynb                        # Geometric Brownian Motion
├── mc_stock_portfolio.ipynb         # Portfolio Monte Carlo
├── stoch_processes.ipynb            # Stochastic processes
├── american_options.ipynb           # LSMC implementation
├── binomial_european.ipynb          # European baseline
├── binomial_model_american.ipynb    # Binomial tree
└── README.md
```

## Method Comparison

### Binomial Trees
**Best for:** Single-asset options, exact early exercise boundary  
**Limitation:** Exponential complexity for multi-asset (curse of dimensionality)

### LSMC
**Best for:** Multi-asset derivatives (baskets, spreads, rainbows)  
**Advantage:** Linear scaling with number of assets

**Example:** For 2 stocks with N=100:
- Binomial needs 100² = 10,000 nodes per time step → intractable
- LSMC uses same 10,000 paths regardless of dimension

## Key Insights

1. **Early exercise** captures interest on strike price K (not speculation)
2. **Vectorization** provides 25x speedup for binomial trees
3. **LSMC regression** estimates continuation value from simulated paths
4. **Both methods converge** to the same price (validates implementation)
5. **Multi-dimensional scaling** makes LSMC essential for real-world derivatives

## Dependencies
```
numpy>=1.20.0
matplotlib>=3.3.0
pandas>=1.2.0
jupyter>=1.0.0
```

## References

- Cox, Ross & Rubinstein (1979) - *Option Pricing: A Simplified Approach*
- Longstaff & Schwartz (2001) - *Valuing American Options by Simulation*
- Hull (2018) - *Options, Futures, and Other Derivatives*


