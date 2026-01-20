# a-simple-random-walk

## About

This repository covers a wide range of subject areas I have used to gain exposure to pricing derivatives. I explored stochastic processes, geometric brownian motion for modelling stock price dynamics and most subsequently building pricing of options based on binomial asset pricing model and least square monte carlo.


**Notebooks:**
- `binomial_model_american.ipynb` - Tree-based pricing with vectorization
- `american_options.ipynb` - Complete LSMC implementation
- `binomial_european.ipynb` - European option baseline
- `gbm.ipynb` - Geometric Brownian Motion foundations
- `stoch_processes.ipynb` - Stochastic process simulations
- `mc_stock_portfolio.ipynb` - Portfolio-level Monte Carlo


## Project Structure
```
.
├── american_options.ipynb           # LSMC implementation
├── binomial_european.ipynb          # European baseline
├── binomial_model_american.ipynb    # Binomial tree pricing
├── understanding_bm/
│   ├── gbm.ipynb                    # Geometric Brownian Motion
│   ├── mc_stock_portfolio.ipynb     # Portfolio Monte Carlo
│   └── stoch_processes.ipynb        # Stochastic processes
└── README.md
```

## Key Insights

1. **Early exercise** captures interest on strike price K (not speculation)
2. **Vectorization** provides 25x speedup for binomial trees
3. **LSMC regression** estimates continuation value from simulated paths
4. **Both methods converge** to the same price (validates implementation)
5. **Multi-dimensional scaling** makes LSMC essential for real-world derivatives

## References

- Cox, Ross & Rubinstein (1979) - *Option Pricing: A Simplified Approach*
- Longstaff & Schwartz (2001) - *Valuing American Options by Simulation*
- Hull (2018) - *Options, Futures, and Other Derivatives*


