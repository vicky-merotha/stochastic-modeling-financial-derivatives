# Stochastic Modeling of Financial Derivatives

**Quantitative Finance | Option Pricing | Stochastic Processes | Volatility Modeling**

**Research project — Stamatics Society, IIT Kanpur**  
**Author:** Vicky Merotha

> **Research question:** How can we estimate the fair value of an option when the underlying asset price is uncertain—and how can we improve on constant-volatility assumptions using market data?

## Project at a glance

| Component | Approach | Reported result |
|---|---|---|
| Asset-price modeling | Geometric Brownian Motion (GBM) | Modeled stochastic asset-price evolution |
| Baseline option valuation | Black–Scholes–Merton framework | Derived the pricing PDE |
| Simulation-based pricing | Monte Carlo option-pricing simulations | **50,000+ simulations** |
| Stochastic volatility | Heston model calibrated to market data | **Within 5% option-pricing error** |
| Volatility surface | Implied-volatility surface fitting | **R² = 0.94** |

*Results above are reported in the project description on my resume. The original notebooks, dataset details, and evaluation artifacts should be attached to this repository before treating it as independently reproducible.*

## 1. Problem statement

Derivative prices depend on uncertain future asset prices, volatility, interest rates, time to maturity, and contract terms. The Black–Scholes–Merton model provides an important analytical baseline, but its constant-volatility assumption does not fully capture the volatility smile observed in markets.

This project studies option valuation from a stochastic-process perspective, progressing from GBM and Black–Scholes to Monte Carlo pricing and the Heston stochastic-volatility framework.

## 2. Research workflow

```text
Financial theory + market observations
                |
                v
     Model asset prices with GBM
                |
                v
   Derive Black–Scholes–Merton PDE
                |
                v
  Run 50,000+ Monte Carlo simulations
                |
                v
 Calibrate Heston model to market data
                |
                v
 Fit and evaluate implied-volatility surface
                |
                v
   Compare model behavior and pricing errors
```

## 3. Mathematical foundations

### 3.1 Geometric Brownian Motion

The baseline asset-price process is

$$
dS_t = \mu S_t\,dt + \sigma S_t\,dW_t,
$$

where $S_t$ is the asset price, $\mu$ is the drift, $\sigma$ is volatility, and $W_t$ is a Wiener process. Under the risk-neutral measure, the drift is replaced by the appropriate risk-neutral rate (for example, $r$ for a non-dividend-paying asset).

### 3.2 Black–Scholes–Merton

For a non-dividend-paying underlying, the option-value PDE is

$$
\frac{\partial V}{\partial t}
+\frac12\sigma^2 S^2\frac{\partial^2 V}{\partial S^2}
+rS\frac{\partial V}{\partial S}
-rV=0.
$$

This provides a theoretical reference for option valuation under constant volatility.

### 3.3 Monte Carlo option pricing

Under risk-neutral simulation, the value of a European call can be estimated by

$$
\widehat C_0=e^{-rT}\frac1N\sum_{i=1}^{N}\max(S_T^{(i)}-K,0).
$$

The project ran **more than 50,000 Monte Carlo simulations** for option pricing. Simulation-based valuation is flexible, although estimates carry sampling error and require convergence checks.

### 3.4 Heston stochastic volatility

Unlike Black–Scholes, the Heston model allows variance to evolve stochastically:

$$
\begin{aligned}
dS_t &= rS_t\,dt+\sqrt{v_t}S_t\,dW_t^S,\\
dv_t &= \kappa(\theta-v_t)\,dt+\xi\sqrt{v_t}\,dW_t^v,\\
d\langle W^S,W^v\rangle_t &= \rho\,dt.
\end{aligned}
$$

Here $v_t$ is instantaneous variance, $\kappa$ is mean reversion, $\theta$ is long-run variance, $\xi$ is volatility of variance, and $\rho$ is the correlation between shocks. **The project calibrated the Heston model to market data and reported option-pricing errors within 5%.**

### 3.5 Implied-volatility surface

An implied-volatility surface describes how market-implied volatility changes with strike (or moneyness) and maturity. The fitted surface achieved a **reported R² of 0.94**, supporting a better representation of volatility-smile behavior than the constant-volatility baseline.

## 4. Reported outcomes

- Built stochastic models for derivative pricing and volatility estimation using mathematical theory and real market data.
- Modeled asset prices with GBM and derived the Black–Scholes–Merton PDE.
- Conducted **50K+ Monte Carlo simulations** for option pricing.
- Calibrated the **Heston stochastic-volatility model**, with reported pricing errors **within 5%**.
- Fitted an **implied-volatility surface (R² = 0.94)** to capture the volatility smile more effectively than the constant-volatility Black–Scholes assumption.

**Evaluation note:** The exact dataset, contract universe, error metric, train/test split, calibration procedure, and R² calculation are not specified in the available project summary. These should be documented from the original work before making stronger performance or out-of-sample claims.

## 5. Visualizations and evidence

Add genuine outputs from the original project here:

1. **GBM simulated asset-price paths** — demonstrate uncertainty across trajectories.
2. **Monte Carlo convergence plot** — show estimated option price versus simulation count, ideally alongside a Black–Scholes benchmark.
3. **Market versus Heston model option prices** — illustrate calibration fit and residual errors.
4. **Implied-volatility surface** — show strike/moneyness and maturity axes, and label whether the surface is market-observed or model-fitted.

> **For a video screen share:** Start at the results table, scroll through the workflow and Heston equations, then show your *actual* simulation and volatility-surface plots once added.

## 6. Key takeaways

1. **Uncertainty must be modeled explicitly.** GBM and Monte Carlo simulations connect probability theory with option valuation.
2. **Model assumptions matter.** Constant volatility is a useful starting point but cannot fully describe observed volatility smiles.
3. **Calibration is as important as theory.** A model should be checked against market observations rather than judged solely on mathematical elegance.
4. **Reported fit is not trading profitability.** Pricing accuracy does not by itself establish a profitable trading strategy or robust out-of-sample performance.

## 7. Reproducibility status

This README documents the scope and reported results of the project. **The original code, market-data sources, calibration configuration, plots, and execution instructions have not yet been provided here.** Once those materials are available, this section can be replaced with verified installation and reproduction steps.

## About

**Vicky Merotha**  
Final-year undergraduate, Indian Institute of Technology Kanpur  
Research project: Stamatics Society, IIT Kanpur

---

*Research and educational use only. Not financial or investment advice.*
